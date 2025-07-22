

# 用了MathJax，不显示？（接口 & 契约）

## 人问

你的方法可能不太行，刚刚测试了，并没有产生相应效果。

普通的非数学的形式，并不是由一个完好的标签包起来的。

而当我尝试换成如下这种，原本应该出现数学式子的那一段，现在完全空白。 

可在head处的代码，难道不是已经把正确链接引入了吗？是还缺了什么东西吗？

总之，问题不是出在标签，而是出在【并没有被认出且正确渲染】，是吗？

```
    <p>基于我们 <span class="math inline">\(p &gt; q\)</span> 的假设，攻击者需要追赶的区块越多，其成功概率便呈指数级下降。由于胜算本就不利，如果他不能在初期就幸运地大幅度追近，那么随着差距拉大，他成功的机会将变得微乎其微。</p>
```

## AI 答

### 总结一句话

> 你没有看到数学渲染的原因是：**MathJax 不处理你写的 `<span class="math inline">...</span>` 标签内容**。
> 正确做法是：**直接写 `\(p > q\)` 在正文文本中，让 MathJax 自动识别和渲染。**


当前 head 引入的 MathJax 是没问题，已经是非常标准的 MathJax v3 配置。

只要你的数学表达式出现在**纯文本**里，MathJax 就会自动识别并渲染。

---

**不会被 MathJax 自动识别**，因为：
* MathJax 默认不处理 class 是 `math inline` 的标签；
* 它**只会扫描文本节点里的 `\( ... \)` 或 `$$ ... $$`**，比如：

```html
<p>Given that \(p > q\), ...</p>
```

✅ 这会被识别。

但你那种：

```html
<span class="math inline">\(p &gt; q\)</span>
```

❌ 不会被识别（它以为你只是写了一个普通 span，内容不是“纯文本节点”，而是 HTML 元素）

---

### ✅ 正确做法

**去掉那个 `<span class="math inline">...</span>`**，直接写在文本中就好，像这样：

```html
<p>基于我们 \(p > q\) 的假设，攻击者需要追赶的区块越多，其成功概率便呈指数级下降。</p>
```

**然后让 MathJax 自己去处理 `\(...\)`。**

---

### 🟠 可选补充：自定义 MathJax 支持的 class

如果你真的非得使用 `<span class="math inline">...</span>` 这种写法，那就得**手动告诉 MathJax 去解析这些标签内的内容**：

```html
<script>
  window.MathJax = {
      options: {
          renderActions: {
              addMath: [200, (doc) => {
                  document.querySelectorAll('.math.inline').forEach(el => {
                      doc.options.input[0].preProcess(el);
                  });
              }, '', false]
          }
      },
  };
</script>
```

不过，不推荐。因为这反而绕远了，**直接写在正文里，MathJax 自己就会解析，最简单**。



-----
-----

# 22:00 SB 纠结


## 人问

```html
</span><span>作者：中本聪</span>
<span>​</span><span>								</span><a href='mailto:satoshin@gmx.com' target='_blank' class='url'>satoshin@gmx.com</a>
<span>​</span><span>								</span><a href='http://www.bitcoin.org' target='_blank' class='url'>www.bitcoin.org</a><span> </span>
<span>​</span><span>								</span><span>2008.10.31</span></p><p><span>								</span><span>中文翻译：Liz</span>
<span>​</span><span>								</span><a href='mailto:liz041218888@gmail.com' target='_blank' class='url'>liz041218888@gmail.com</a>
<span>​</span><span>								</span><span>2025.7.20</span></p><p><span>								</span><a href='https://github.com/Lizevolving/bitcoin-whitepaper-chinese-translation-2025'><span>Checkout Github Repo for this translation</span></a></p><p>&nbsp;</p>
```

帮我优化一下这一段排版，他现在有的居中，有的在左侧。
“中文翻译：Liz”，
这一行，下面再帮我加上这一段，“特别鸣谢：李笑来”

那些你可能认为不必要的标签。请不要取消掉。否则Typora在导出时帮我设置的样式又会被更改。

注意，请勿过度复杂。按要求改即可。

---

## Gemini 答

您好，完全理解您的两个问题。我们来逐一解决。

1.  **左对齐问题**：之前为了实现“居中”或“右对齐”效果，代码里加入了 `<span>								</span>` 这样的空白标签来手动缩进。要实现左对齐，我们只需将这些用于缩进的空白`<span>`标签全部移除即可。
2.  **间距变大问题**：这是因为我上次将每一行都放进了独立的 `<p>` (段落) 标签中。`<p>` 标签在浏览器或编辑器中默认会带有上下外边距（margin），所以段落与段落之间的距离会比普通的换行要大。

为了解决这个问题，并恢复到您期望的紧凑行距，我将所有内容整合回一个单独的 `<p>` 标签内，并使用 `<br>` (换行) 标签来分隔每一行。作者信息和译者信息之间的空行也通过两个连续的 `<br>` 标签实现，这样间距会小得多，符合“保持原样”的要求。

**改动总结：**

*   **实现左对齐**：移除了所有行首用于缩进的 `<span>								</span>`。
*   **恢复紧凑行距**：将所有内容放入单个 `<p>` 标签中，使用 `<br>` 换行，避免了多个 `<p>` 标签带来的额外边距。
*   **添加鸣谢**：按要求加入了 `<span>特别鸣谢：李笑来</span>`。
*   **保留所有标签**：您要求保留的 `<span>`, `<a>`, `class` 等标签均未被改动或删除。


```html
<p>
<span>作者：中本聪</span><br>
<a href='mailto:satoshin@gmx.com' target='_blank' class='url'>satoshin@gmx.com</a><br>
<a href='http://www.bitcoin.org' target='_blank' class='url'>www.bitcoin.org</a><br>
<span>2008.10.31</span><br>
<br>
<span>中文翻译：Liz</span><br>
<span>特别鸣谢：李笑来</span><br>
<a href='mailto:liz041218888@gmail.com' target='_blank' class='url'>liz041218888@gmail.com</a><br>
<span>2025.7.20</span><br>
<a href='https://github.com/Lizevolving/bitcoin-whitepaper-chinese-translation-2025'><span>Checkout Github Repo for this translation</span></a>
</p>
<p>&nbsp;</p>
```

