# exitcode

**给命令行工具的退出码语义算一个特征指纹并定位可疑片段。**

`exitcode` —— 通过字符级与结构级特征识别命令行工具的退出码语义的痕迹，给出密度与命中位置

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`exitcode.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install mcadvent-exitcode
```

装完直接用命令名调用：

```bash
exitcode --help
```

也可以不用安装，直接把 `exitcode.py` 拷走用——它只依赖标准库。

## 为什么需要它

只做特征匹配不做语义判定，所以不会被同义改写绕过

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 命令行工具的退出码语义 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python exitcode.py --file input.txt
python exitcode.py --text "示例内容"
python exitcode.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 相似度按字符与词估算，不等于向量相似度。
- 不联网，不做语义检索。

## 跑测试

```bash
python test_exitcode.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/mcadvent/exitcode>

---

## 关于作者

mcadvent 做命令行工具的退出码语义相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://mcadvent.github.io>
- 仓库：<https://github.com/mcadvent/exitcode>

## 许可

MIT，见 [LICENSE](LICENSE)。
