.. _cn_api_paddle_nn_BCELoss:

BCELoss
-------------------------------

.. py:class:: paddle.nn.BCELoss(weight=None, reduction='mean', name=None)

该接口用于创建一个BCELoss的可调用类，用于计算输入 ``input`` 和标签 ``label`` 之间的二值交叉熵损失值。二值交叉熵损失函数公式如下：

当 `weight` 不为空时，公式为：

.. math::
  Out = -1 * weight * (label * log(input) + (1 - label) * log(1 - input))

当 `weight` 为空时，公式为：

.. math::
  Out = -1 * (label * log(input) + (1 - label) * log(1 - input))

当 `reduction` 为 `none` 时，直接返回最原始的 `Out` 结果。

当 `reduction` 为 `mean` 时，最终的输出结果为：

.. math::
  Out = MEAN(Out)

当 `reduction` 为 `sum` 时，最终的输出结果为：

.. math::
  Out = SUM(Out)


.. note::
    输入数据 ``input`` 一般是 ``sigmoid`` 的输出。因为是二分类，所以标签值 ``label`` 应该是0或者1。

参数
:::::::::
    - **weight** (Tensor，可选) - 手动指定每个batch二值交叉熵的权重，如果指定的话，维度必须是一个batch的数据的维度。数据类型是float32, float64。默认值是：None。
    - **reduction** (str，可选) - 指定应用于输出结果的计算方式，可选值有：``'none'``, ``'mean'``, ``'sum'``。默认为 ``'mean'``，计算 `BCELoss` 的均值；设置为 ``'sum'`` 时，计算 `BCELoss` 的总和；设置为 ``'none'`` 时，则返回bce_loss。
    - **name** (str，可选) - 具体用法请参见 :ref:`api_guide_Name`，一般无需设置，默认值为 None。

形状
:::::::::
    - **input** (Tensor) - :math:`(N, *)`，其中N是batch_size， `*` 是任意其他维度。输入数据 ``input`` 一般是 ``sigmoid`` 的输出。数据类型是float32、float64。
    - **label** (Tensor) - :math:`(N, *)`，标签 ``label`` 的维度、数据类型与输入 ``input`` 相同。
    - **output** (Tensor) - 输出的Tensor。如果 :attr:`reduction` 是 ``'none'``，则输出的维度为 :math:`(N, *)`，与输入 ``input`` 的形状相同。如果 :attr:`reduction` 是 ``'mean'`` 或 ``'sum'``，则输出的维度为 :math:`[1]` 。

返回
:::::::::
    返回计算BCELoss的可调用对象。

代码示例
::::::::::

COPY-FROM: paddle.nn.BCELoss