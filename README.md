# rename-cli

一个用来批量重命名的命令行工具，主要是解决我遇到的问题。

计划支持以下用法：

rename [输入] 输出  [-config]
默认处理当前目录下全部内容，且直接覆盖输出文件。

如果只有一个参数，会被当做输出。

输入输出会和默认配置、自定义配置进行合并，规则是 `输入 > 自定义 > 默认配置`。之前进行效验。
会优先根据配置项中的内容进行一一映射，如果没有映射配置项，会读取变量。如果映射配置项为空、且输出不包含变量，则不会进行修改。

输入基于 fast-glob 进行匹配（仅支持第一个参数，字符串或数组） ，输出基于 fs-extra。

默认不替换后缀

例外情况： 默认.开通的不处理，文件夹不处理，默认 配置文件 不处理（.rename.config.json 或传参指定的 ），默认 node_modules 目录下的不处理
