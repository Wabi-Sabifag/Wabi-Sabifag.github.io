---
title: MockingBir
date: 2023-02-06 22:56:14
description: # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: Python   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- Python #文章标签  
- AI
categories: 
- Python       #文章分类
- GitHub-Openner
- AI
keywords:   #页面关键词
cover:  'img/46.jpg'   #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）
comments:         #显示页面评论模块 默认 true
top_img:  'img/46.jpg'         #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）

copyright: false                          #显示文章版权模块
copyright_author: Wabi-Sabifag          #文章版权模块的文章作者
copyright_author_href:                  #文章版权模块的链接
copyright_url: 'https://Wabi-Sabifag.github.io'
copyright_info: 此文章版权归Wabi-Sabifag所有。如有转载，请注明来自原作者(但万物开源)  #文章版权模块的文字

---
# MockingBir的部署

###### 开源作者：babysor

操作系统：Win10

硬件：cpu

2.安装

> 如果已经确认安装过，请忽略该步骤

* 获取[GitHub开源代码库](https://github.com/babysor/MockingBird)
  
* 安装Anacodna， Python 3.8 或更高，参考[中文教程](https://zhuanlan.zhihu.com/p/348120084)，在Anaconda中创建并切换到独立虚拟环境后，进行以下步骤。
  
* 安装 PyTorch， 直接[官网下载](https://pytorch.org/get-started/locally/)。
  

> 验证本步骤是否成功：在系统任意路径下运行python，进入交互式编程界面后输入 `import torch;`, 回车， `torch.cuda.is_available()`, 回车。如果都是成功的话，可以进行下一步。

![torch1](https://github.com/babysor/MockingBird/wiki/imgs/torch1.png)

* 安装 ffmpeg。 1）[下载](http://ffmpeg.org/download.html#build-windows) 选择点击打开链接Windows对应的版本下载 2）解压 ffmpeg-xxxx.zip 文件到指定目录； 3）将解压后的文件目录中 bin 目录（包含 ffmpeg.exe ）添加进 path 环境变量中； 4）进入 cmd，输入 ffmpeg -version，可验证当前系统是否识别 ffmpeg 以及查看 ffmpeg 的版本
  
* 运行pip install -r requirements.txt 来安装剩余的必要包。
  

> 确保本步骤不报错

* 安装 webrtcvad 用 pip install webrtcvad-wheels。

> 确保本步骤不报错

3.下载社区训练好的模型

在以下选择中下载模型

| 作者  | 下载链接 |
| --- | --- |
| @miven | [百度网盘 请输入提取码](https://pan.baidu.com/s/1PI-hM3sn5wbeChRryX-RCQ) 提取码：2021 |

> 该模型与最新代码有兼容性问题 请查阅 https://github.com/babysor/MockingBird/issues/37 解决

下载完成后，确保 `xxx.pt` 格式的文件放在代码库的 `synthesizer\saved_models`文件夹下，`saved_models`如不存在请新建

4.运行demo_toolbox

在代码库路径下，运行 `python demo_toolbox.py -d .\samples` 尝试使用工具箱, 由于没有下载任何数据集，这里的功能比较简单：

1. 确保界面左边中间的 `synthesizer` 选择了上一步中 `xxx.pt` 文件对应的模型。
  
2. 点击`Record`录入你的5秒语音
  
3. 输入任意文字
  
4. 点击 `Synthesizer and vocode` 等待效果输出较简单：
  
5. 确保界面左边中间的 `synthesizer` 选择了上一步中 `xxx.pt` 文件对应的模型。
  
6. 点击`Record`录入你的5秒语音
  
7. 输入任意文字
  
8. 点击 `Synthesizer and vocode` 等待效果输出
  

# 5.遇到的问题总结

1.元数据流报错:

        在CSDN找到下面的方式无法解决问题。

    pip install setuptools==57.5.0 -i https://pypi.tuna.tsinghua.edu.cn/simple 

       解决：

        在对比开源作者的文件时，发现作者main主支内容和本地文件不一致，在其他分支有完整的项目。

2.  报错：

     cpu硬件没有运行，以及文件的训练数据无法找到。

    
    Arguments:
        datasets_root:    None
        enc_models_dir:   encoder\saved_models
        syn_models_dir:   synthesizer\saved_models
        voc_models_dir:   vocoder\saved_models
        cpu:              False
        seed:             None
        no_mp3_support:   False
    
    Warning: you did not pass a root directory for datasets as argument.
    The recognized datasets are:
            LibriSpeech/dev-clean
    

        解决：

            将 开发者提供的云盘资料下级文件全部导入该项目的主项目下，不用像作者要求的创建文件夹。

                我自行创建文件夹同时将所有文件放在 /saved_models 下，反而导致文件的路径出错。