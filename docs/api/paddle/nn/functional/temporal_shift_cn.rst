.. _cn_api_fluid_layers_temporal_shift:

temporal_shift
-------------------------------
.. py:function:: paddle.nn.functional.temporal_shift(x, seg_num, shift_ratio=0.25, name=None, data_format="NCHW")


该OP用于对输入X做时序通道T上的位移操作，为TSM(Temporal Shift Module)中使用的操作。

输入（X）的形状应为[N*T, C, H, W]或[N*T, H, W, C]，N是批大小，T是 ``seg_num`` 指定的时间段号，C是通道号，H和W是特征的高度和宽度。

以 data_format="NCHW" 为例，时间偏移计算如下：

步骤1：将输入（X）reshape为[N, T, C, H, W]。

步骤2：填充0到第二个(T)尺寸的变形结果，填充宽度每边为1，填充结果的形状为[N，T+2，C，H，W]。

步骤3：假设 ``shift_ratio`` 为1/4，切片填充结果如下：

.. math::

    slice1 &= x[:, :T, :C/4, :, :]

    slice2 &= x[:, 2:T+2, C/4:C/2, :, :]

    slice3 &= x[:, 1:T+1, C/2:, :, :]

步骤4：沿第3(C)维连接三个切片，并将结果重塑为[N*T, C, H, W]。

有关时序移动的详细信息，请参阅文件：`Temporal Shift Module <https://arxiv.org/abs/1811.08383>`_ 

参数
:::::::::
  - **x**  (Tensor) – 时移算符的输入张量。维度为 :math:`[N*T，C，H，W]` 的4-D Tensor。N为批量大小，T为时间段数，C为信道数，H为特征高度，W为特征宽度，数据类型为float32或float64。
  - **seg_num**  (int) – 时间段编号，这应该是一个正整数。
  - **shift_ratio**  (float) – 通道的移位比、通道的第一个 ``shift_ratio`` 部分沿时间维度移动-1，通道的第二个 ``shift_ratio`` 部分沿时间维度移动1，范围须在[0, 0.5]内。默认值0.25
  - **name** (str，可选) - 具体用法请参见 :ref:`api_guide_Name`，一般无需设置，默认值为 None。
  - **data_format** (str，可选) - 指定输入的数据格式，输出的数据格式将与输入保持一致，可以是"NCHW"或"NHWC"。N是批尺寸，C是通道数，H是特征高度，W是特征宽度。默认值："NCHW"。

返回
:::::::::
Tensor，时序位移后的输出张量，维度和数据类型与输入 ``x`` 一致。

代码示例
:::::::::

COPY-FROM: paddle.nn.functional.temporal_shift