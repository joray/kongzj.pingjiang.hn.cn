---
layout: post
category : Pyramid
title: Pyramid
tagline: ""
tags : [Python, Pyramid]
---
{% include JB/setup %}




WINDOWD 
CMD.EXE

python 路径添加环境变量
git 路径添加环境变量

D:\Program Files\Python36\Scripts\;
D:\Program Files\Python36\;
C:\Program Files\Git\bin

    SET PATH=C:\Program Files\Python 3.6;%PATH%
    SET VENV=D:\Application\blogr_tutorial\env
    python -m venv %VENV%
    %VENV%\Scripts\pip install "pyramid==1.9.1"
    
    %VENV%\Scripts\pip install --user cookiecutter
