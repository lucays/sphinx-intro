=====================
reStructuredText简介
=====================


标题
=========

| 和Markdown不同，reStructuredText中的标题只需要在文本下一行加上特殊字符如\ ``=-`:.'"~^_*+#``\ 即可，字符长度应大于或等于标题长度。
| 多级标题只需要使用不同的特殊字符，解析器会把第一个特殊字符渲染为一级标题，第二个为二级标题，之后以此类推。

.. code::

    一级标题
    =========

    二级标题
    ---------

    三级标题
    *********

.. note::

    这么设计对比Markdown的好处之一是，如果在文档的中后期想把之前的章节汇总成一卷（在最初加上一级标题），只需要在最初使用不同的特殊字符加个标题就好了，而不必去改动所有的\ ``##``\ 为\ ``###``\ ，\ ``###``\ 为\ ``####``\ 等。

引用
======

reStructuredText中的引用只需要使用空格或tab加上空行做出一个区块即可:

    引用区块1

        引用区块2（嵌套）

.. code::

    引用区块1

        引用区块2（嵌套）

列表
======

reStructuredText中的列表语法和Markdown基本一致：

有序列表
---------

2. item1
3. item2
4. item3

.. code::

    2. item1
    3. item2
    4. item3

不需要用1作为起始点

无序列表
---------

- item1
- item2
- item3

.. code::

    - item1
    - item2
    - item3

代码块
=========

reStructuredText调用\ ``pygments``\ 实现语法高亮。

    import requests

    r = requests.get('http://www.baidu.com')
    print(r.text)

.. code::

    .. code::

        import requests

        r = requests.get('http://www.baidu.com')
        print(r.text)

超链接
=========

超链接的实现略微复杂，有两种：

- 行内：

    这是\ `Sphinx <https://www.sphinx-doc.org/en/master/>`__\ 官方文档的网页。

    .. code::

        这是\ `Sphinx <https://www.sphinx-doc.org/en/master/>`__\ 官方文档的网页。

- 换行：

    这是\ `Sphinx`_\ 官方文档的网页。

    .. _Sphinx: https://www.sphinx-doc.org/en/master/

    .. code::

        这是\ `Sphinx`_\ 官方文档的网页。

        .. _Sphinx: https://www.sphinx-doc.org/en/master/

取消前后的\ ``\``\ 标记时，前后必须加上空格表示这是reStructuredText标记：

这是 `Sphinx <https://www.sphinx-doc.org/en/master/>`__ 官方文档的网页。

.. code::

    这是 `Sphinx <https://www.sphinx-doc.org/en/master/>`__ 官方文档的网页。

这是`Sphinx <https://www.sphinx-doc.org/en/master/>`__官方文档的网页。

.. code::

    这是`Sphinx <https://www.sphinx-doc.org/en/master/>`__官方文档的网页。

行内标记
=========

- 强调，通常渲染成斜体。\ ``*被强调的*``\ → \ *被强调的*\
- 重点强调，通常加粗。\ ``**被强调的**``\ → \ **被强调的**\
- 原始文本，可用于代码。\ ````代码````\ → \ ``代码``\
- 脚注，不一定放在文章末尾，位置可自定。\ ``注 [#]_``\ → \ 注 [#]_\
- 引文，即指定了标签的脚注。\ ``引文 [NT202020]_``\ → \ 引文 [NT202020]_\

.. [#] 这是脚注。

.. [NT202020] 这是引文。

索引跳转
=========

当前页的标题可以简单的使用\ ``标题_``\的格式来跳转，如跳转到\ 引用_\ 。

要跳转到其他页面的各级标题，需要先在那些页面标题上方加上一行\ ``.. _标题``\ ，然后可以使用\ ``:ref:`标题```\ 的形式来跳转，如跳转到\ :ref:`首页`\ 。

图片
=======

插入图片可以用\ ``figure``\或\ ``image``\ ，前者可以指定图片标题和说明文字。参数用\ ``target``\ 可以为图片添加可点击的链接，也可以链接到另一张图片，如点击图片（缩略图）显示原图：

.. figure:: ../_static/c02/parrot_thumbnail.jpg
   :align: center
   :target: ../_static/c02/parrot.jpg

   *金刚鹦鹉*

.. code::

    .. figure:: ../_static/c02/parrot_thumbnail.jpg
        :align: center
        :target: ../_static/c02/parrot.jpg

        *金刚鹦鹉*

表格
=========

Grid Tables，支持跨行跨列:

+------------------------+------------+----------+----------+
| Header row, column 1   | Header 2   | Header 3 | Header 4 |
| (header rows optional) |            |          |          |
+========================+============+==========+==========+
| body row 1, column 1   | column 2   | column 3 | column 4 |
+------------------------+------------+----------+----------+
| body row 2             | Cells may span columns.          |
+------------------------+------------+---------------------+
| body row 3             | Cells may  | - Table cells       |
+------------------------+ span rows. | - contain           |
| body row 4             |            | - body elements.    |
+------------------------+------------+---------------------+

.. code::

    +------------------------+------------+----------+----------+
    | Header row, column 1   | Header 2   | Header 3 | Header 4 |
    | (header rows optional) |            |          |          |
    +========================+============+==========+==========+
    | body row 1, column 1   | column 2   | column 3 | column 4 |
    +------------------------+------------+----------+----------+
    | body row 2             | Cells may span columns.          |
    +------------------------+------------+---------------------+
    | body row 3             | Cells may  | - Table cells       |
    +------------------------+ span rows. | - contain           |
    | body row 4             |            | - body elements.    |
    +------------------------+------------+---------------------+

Simple Tables:

=====  =====  ======
   Inputs     Output
------------  ------
  A      B    A or B
=====  =====  ======
False  False  False
True   True   True
=====  =====  ======

.. code::

    =====  =====  ======
    Inputs     Output
    ------------  ------
    A      B    A or B
    =====  =====  ======
    False  False  False
    True   True   True
    =====  =====  ======
