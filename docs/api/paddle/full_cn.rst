.. _cn_api_tensor_full:

full
-------------------------------

.. py:function:: paddle.full(shape, fill_value, dtype=None, name=None)



创建形状大小为 ``shape`` 并且数据类型为 ``dtype``  的Tensor，其中元素值均为 ``fill_value`` 。

参数
::::::::::::

    - **shape** (list|tuple|Tensor) – 指定创建Tensor的形状(shape)，数据类型为int32 或者int64。
    - **fill_value** (bool|float|int|Tensor) - 用于初始化输出Tensor的常量数据的值。注意：该参数不可超过输出变量数据类型的表示范围。
    - **dtype** （np.dtype|str，可选）- 输出变量的数据类型。若为None，则输出变量的数据类型和输入变量相同，默认值为None。
    - **name** (str，可选) - 具体用法请参见 :ref:`api_guide_Name`，一般无需设置，默认值为 None。
    
返回
::::::::::::
返回一个存储结果的Tensor，数据类型和dtype相同。


代码示例
::::::::::::

COPY-FROM: paddle.full:code-example1
