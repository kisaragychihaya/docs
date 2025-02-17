.. _cn_api_nn_layer_Sigmoid:

Sigmoid
-------------------------------

.. py:class:: paddle.nn.Sigmoid(name=None)

该接口用于创建一个 ``Sigmoid`` 的可调用类。这个类可以计算输入 `x` 经过激活函数 `sigmoid` 之后的值。

    .. math::

        output = \frac{1}{1 + e^{-x}}

参数
::::::::
  - **name** (str，可选) - 具体用法请参见 :ref:`api_guide_Name`，一般无需设置，默认值为 None。

形状
::::::::
  - **x** （Tensor）- N-D tensor，可以支持的数据类型是float16，float32，float64。 

返回
::::::::
  返回计算 ``Sigmoid`` 的可调用对象。


代码示例
::::::::

COPY-FROM: paddle.nn.Sigmoid