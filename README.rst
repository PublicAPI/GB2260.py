|GB/T 2260| |Build Status| |Coverage Status| |PyPI Version| |Wheel Status|

GB2260
======

The Python implementation for looking up the Chinese administrative divisions.


Installation
------------

::

    $ pip install GB2260


Basic Usage
-----------

The way to look up a administrative division by its GB2260 code is
the basic interface ``gb2260.get(code)``:

.. code-block:: python

    >>> import gb2260
    >>>
    >>> division = gb2260.get(360426)
    >>> print(division)
    <gb2260.Division 360426 江西省/九江市/德安县>

The data of a division is accessible to interfaces as following:

.. code-block:: python

    >>> division.code
    u'360426'
    >>> division.name
    u'德安县'
    >>> division.is_county
    True
    >>> division.is_province
    False
    >>> division.is_prefecture
    False
    >>> print(division.province)
    <gb2260.Division 360000 江西省>
    >>> print(division.prefecture)
    <gb2260.Division 360400 江西省/九江市>
    >>> print(division.county)
    <gb2260.Division 360426 江西省/九江市/德安县>

The hierarchic divisions could be generated with a iterator method:

.. code-block:: python

    >>> division.stack()
    <generator object stack at 0x103e26a50>
    >>> for current in division.stack():
    ...     print(u'{0} {1}'.format(current.name, current.code))
    江西省 360000
    九江市 360400
    德安县 360426


Issues
------

If you want to report bugs or request features, please create issues on
`GitHub Issues <https://github.com/cn/GB2260/issues>`_.


External Links
--------------

- `GB/T 2260-2002 in Wikipedia <https://zh.wikipedia.org/zh-cn/GB/T_2260-2002>`_
- `Codes for administrative divisions of PRC <http://www.stats.gov.cn/tjsj/tjbz/xzqhdm/201401/t20140116_501070.html>`_

.. |GB/T 2260| image:: http://img.shields.io/badge/GB%2FT-2260-blue.svg?style=flat
   :target: https://github.com/cn/GB2260
   :alt: GB/T 2260
.. |Build Status| image:: https://img.shields.io/travis/cn/GB2260.py.svg?style=flat
   :target: https://travis-ci.org/cn/GB2260.py
   :alt: Build Status
.. |Coverage Status| image:: https://img.shields.io/coveralls/cn/GB2260.py.svg?style=flat
   :target: https://coveralls.io/r/cn/GB2260.py
   :alt: Coverage Status
.. |Wheel Status| image:: https://pypip.in/wheel/GB2260/badge.svg?style=flat
   :target: https://warehouse.python.org/project/GB2260
   :alt: Wheel Status
.. |PyPI Version| image:: https://img.shields.io/pypi/v/GB2260.svg?style=flat
   :target: https://pypi.python.org/pypi/GB2260
   :alt: PyPI Version
