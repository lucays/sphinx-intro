=================
readthedocs支持
=================

把文档发布在github/gitee等平台后，通过一些设置，可以实现每次git push后自动构建到readthedocs上。

启用webhook
=============

1. 首先，得注册readthedocs帐号
2. 在右上角帐号菜单中点击“我的项目”
3. 点击import project
4. 点击右侧手动导入，填写项目名、项目地址，然后点击“下一页”

导入完成，会自动启用webhook，接着每次push都可以自动构建了。

项目管理
=============

默认的管理一般无需改动，高频设置也就python版本和生成pdf/epub以及重定向等选项。

搜索
========

安装readthedocs-sphinx-search:

.. code::

    pip install git+https://github.com/readthedocs/readthedocs-sphinx-search@master

修改conf.py:

.. code::

    extensions = [
        'sphinx_search.extension',
    ]

下载pdf等
=============
