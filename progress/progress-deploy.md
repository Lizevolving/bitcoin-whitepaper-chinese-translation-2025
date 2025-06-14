好问题。你的思路非常清晰，直指要害。

那个 `pandoc` 命令是完美的**起点**，但它生成的是一个**静态文件**。你要求的功能——主题切换、语言切换——都是**动态**的。

因此，我们的方案是：**以静态为骨，注入少量动态之魂。**

### 一、 你没想到的要点（克制但关键）

在你的要求之上，再加三点，就能让这个页面真正**不朽**。

1.  **导航性 (Navigability):** 白皮书不短。在侧边提供一个随页面滚动的**目录**（Table of Contents），点击即可跳转。这是对长文阅读最基本的尊重。Pandoc可以一键生成。
2.  **状态持久化 (State Persistence):** 用户选择了暗黑模式，刷新页面或下次再来，应该还是暗黑模式。语言选择同理。这需要用到浏览器的 `localStorage`。只需几行代码，体验天差地别。
3.  **内容可分离标记 (Content Delimiters):** 这是实现语言切换最干净的**前提**。在你的 Markdown 源文件中，用最简单的方式把中英文内容块分开。Pandoc 的 Fenced Divs 语法是天赐之选：

    ```markdown
    ::: en
    Abstract. A purely peer-to-peer version of electronic cash...
    :::

    ::: cn
    摘要。一种纯粹的点对点电子现金...
    :::
    ```
    这样做，转换出的HTML会自动带上`<div class="en">`和`<div class="cn">`，为后续用CSS和JS精准控制其显示/隐藏，铺平了道路。

### 二、 如何直接、高效地实现？

忘掉复杂的框架。我们就用三样东西：`HTML` + `CSS` + `纯JavaScript`。

**步骤 1：生成带“骨架”的HTML**

修改你的`pandoc`命令，加入`--toc`（生成目录）和`-s`（生成独立完整HTML文件）。我们暂时不内联CSS，因为要方便修改。

```bash
# --standalone (-s) 创建一个完整的HTML文件
# --toc 创建目录
# --css 指定外部CSS文件
# --metadata title="你的标题" 设置页面标题
pandoc README.md -s --toc --css=style.css --metadata title="Bitcoin Whitepaper" -o index.html
```

同时，确保你的`README.md`已经用上面的 `:::` 语法标记好了中英文区块。

**步骤 2：布局与样式 (style.css)**

你的`style.css`文件包含三部分：

1.  **基础Markdown样式：** 从网上找一个你喜欢的极简`markdown.css`库（如`github-markdown-css`, `awsm.css`等），复制进来作为基础。
2.  **主题切换逻辑：**

    ```css
    /* 默认亮色主题 */
    :root {
      --bg-color: #ffffff;
      --text-color: #333333;
    }

    /* 当html标签有 data-theme="dark" 属性时，应用暗色 */
    [data-theme='dark'] {
      --bg-color: #121212;
      --text-color: #eeeeee;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-color);
    }
    ```
3.  **语言切换逻辑：**

    ```css
    /* 默认中英对照，什么都不用隐藏 */

    /* 当body有.show-en class时，隐藏中文 */
    .show-en .cn { display: none; }

    /* 当body有.show-cn class时，隐藏英文 */
    .show-cn .en { display: none; }
    ```
    
    你还需要一些样式来美化右上角的按钮，这里从简。

**步骤 3：注入灵魂 (JavaScript)**

在 `index.html` 的 `</body>` 结束标签前，加入`<script>`标签，或者链接一个外部JS文件。

```html
<!-- 放在 </body> 前 -->
<script>
document.addEventListener('DOMContentLoaded', () => {
  // --- DOM元素获取 ---
  const themeToggle = document.getElementById('theme-toggle'); // 假设你的主题按钮id是'theme-toggle'
  const langSlider = document.getElementById('lang-slider'); // 语言滑块id是'lang-slider'
  const body = document.body;
  const html = document.documentElement;

  // --- 1. 状态持久化：页面加载时读取localStorage ---
  const currentTheme = localStorage.getItem('theme') || 'light';
  const currentLang = localStorage.getItem('lang') || 'all'; // 'en', 'cn', 'all'
  
  html.setAttribute('data-theme', currentTheme);
  updateLang(currentLang);

  // --- 2. 主题切换 ---
  themeToggle.addEventListener('click', () => {
    const newTheme = html.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
    html.setAttribute('data-theme', newTheme);
    localStorage.setItem('theme', newTheme);
  });

  // --- 3. 语言切换 (用一个0,1,2的range input滑块) ---
  langSlider.addEventListener('input', (e) => {
    const value = e.target.value; // 0=英文, 1=对照, 2=中文
    let lang = 'all';
    if (value == 0) lang = 'en';
    if (value == 2) lang = 'cn';
    updateLang(lang);
    localStorage.setItem('lang', lang);
  });

  function updateLang(lang) {
      body.classList.remove('show-en', 'show-cn');
      if (lang === 'en') body.classList.add('show-en');
      if (lang === 'cn') body.classList.add('show-cn');
      // 设置滑块的初始位置
      if (langSlider.value != (lang === 'en' ? 0 : (lang === 'cn' ? 2 : 1))) {
        langSlider.value = lang === 'en' ? 0 : (lang === 'cn' ? 2 : 1);
      }
  }
});
</script>
</body>
```

### 总结

你的 `index.html` 只需要在右上角放置三个简单的HTML元素：

```html
<div class="controls">
  <button id="theme-toggle">黑/白</button>
  <input type="range" id="lang-slider" min="0" max="2" step="1" value="1"> <!-- 0:EN, 1:ALL, 2:CN -->
  <a href="your-github-repo-url" target="_blank">GitHub</a>
</div>
```

**这个方案的威力在于：**

*   **解耦：** 内容（Markdown）、表现（CSS）、行为（JS）完全分开。
*   **高效：** Pandoc负责繁重的转换工作，JS只做最轻量的交互。
*   **可维护：** 想改样式？只动`style.css`。想更新白皮书内容？只动`README.md`，然后重新跑一遍`pandoc`命令。逻辑完全不变。

这就是朴素、有力、且经得起时间考验的方案。它把复杂性控制在最低，同时实现了你想要的一切，甚至更多。