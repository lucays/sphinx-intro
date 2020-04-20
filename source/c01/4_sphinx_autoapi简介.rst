======================
sphinx-autoapi简介
======================

sphinx-autoapi是一个能自动从项目根目录起提取方法和注释生成文档的项目。除Python外还支持go等语言。

安装
======

.. code::

    pip install sphinx-autoapi

Python使用
===============

在conf.py的扩展中添加：

.. code::

    extensions = ['autoapi.extension']
    autoapi_dirs = ['../mypackage']

此处autoapi_dirs假定文件结构如下，可依据实际情况再作修改：

.. code::

    mypackage/
    ├── docs
    │   ├── _build
    │   ├── conf.py
    │   ├── index.rst
    │   ├── make.bat
    │   ├── Makefile
    │   ├── _static
    │   └── _templates
    ├── mypackage
    │   ├── _client.py
    │   ├── __init__.py
    │   └── _server.py
    └── README.md

这样，再运行make html时，就会自动提取当前项目的方法和注释生成api文档。
