+++
title = "替换文件中的字符串"
author = ""
image = ""
share = true
comments = true
date = "2017-02-08T16:54:24+02:00"
menu = ""
slug = "替换文件中的字符串"
draft = false
tags = ["python","shell"]

+++

**替换文件中的字符串**

将文件中的字符串全部替换，并生成新的文件，如：执行'replace.py ntfs xfs sysInfoin sysInfoout'将把sysInfoin文件中的所有'ntfs'替换为'xfs'并写入sysInfoout文件。

- 代码中使用了 **'*args'** 这样的可变参数列表，参数将以一个元组的形式传递到函数中；在本段代码中对args的tuple数量判断是不必要的，但针对 'replace_text' 这个函数来说这个判断是有必要的；
- 代码中使用了 **with ... as ...** 这样的控制流语句，在 **with** 结束后将自动关闭所打开的文件；

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-
"""Replace string from a file to another file."""

import os
import sys

usage = "Usage: %s search_txt replace_text [infilename [outfiename]]." % os.path.basename(sys.argv[0])

def replace_text( *args):

    opt_args = args[0] if len(args) ==1 else None
    if not opt_args:
        print 'Error : There are %d tuple args in function : ' % len(args), args
        sys.exit(1)
    stext, rtext = opt_args[1], opt_args[2]
    (infile, outfile) = (opt_args[3], opt_args[4]) if len(opt_args) > 4 else (None, None)
    if not infile or not outfile:
        print 'Error : There are %d args in script.' % len(opt_args)
        sys.exit(1)

    with open(infile, 'r') as inputfile:
        with open(outfile, 'w+') as outputfile:
            for line in inputfile:
                outputfile.write(line.replace(stext, rtext))

if __name__ == '__main__':

    if len(sys.argv) < 3:
        print usage
    else:
        replace_text(sys.argv)
```
