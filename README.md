# Markdown to Anki

一个本地运行的 Anki 牌组工具，用于在 Markdown 与 `.apkg` 之间双向转换。

## 功能

- 图形界面支持 Markdown -> Anki 和 Anki -> Markdown。
- 支持单个 Markdown 文件或完整牌组文件夹，文件夹层级自动映射为 subdeck。
- 解析 `### Front`、`### Back` 卡片格式，并支持稳定 ID，便于重复生成和更新卡片。
- 自动处理图片、媒体打包、表格、代码块、原生 HTML、MathJax 和 Mermaid。
- 反向导出时保留卡片媒体、标签、模板信息和往返编辑所需的元数据。
- 图片缺失、格式错误等问题记录为警告，不影响其他卡片继续生成。

## 使用

需要 Python 3.10 或更高版本，并安装依赖：

```powershell
python -m pip install -r requirements.txt
python markdown_to_anki.py
```

启动后选择转换方向、输入文件或牌组文件夹，再选择输出位置。Markdown 卡片基本格式如下：

````markdown
<!-- anki-id: cell-biology-001 -->
### Front
细胞膜的主要功能是什么？

### Back
维持细胞内环境稳定，并控制物质进出细胞。

![细胞膜](media/cell-membrane.png)
````

使用 Anki -> Markdown 时，程序会生成包含 `cards.md` 和 `media` 的文件夹。编辑时请保留导出的 `anki-*` 注释及 `.anki-roundtrip.json`，这样重新打包可以继续更新原卡片。

## 目录结构

```text
细胞生物学/
├─ Ch.01/
│  ├─ cards.md
│  └─ media/
├─ Ch.02/
│  ├─ cards.md
│  └─ media/
└─ 细胞生物学.apkg
```

程序入口和全部转换逻辑位于 `markdown_to_anki.py`。
