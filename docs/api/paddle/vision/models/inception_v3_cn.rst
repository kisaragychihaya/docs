.. _cn_api_paddle_vision_models_inception_v3:

inception_v3
-------------------------------

.. py:function:: paddle.vision.models.inception_v3(pretrained=False, **kwargs)

 InceptionV3模型，来自论文 `"Rethinking the Inception Architecture for Computer Vision" <https://arxiv.org/pdf/1512.00567.pdf>`_ 。

参数
:::::::::
  - **pretrained** (bool，可选) - 是否加载在imagenet数据集上的预训练权重。默认值：False。

返回
:::::::::
InceptionV3模型，Layer的实例。

代码示例
:::::::::
COPY-FROM: paddle.vision.models.inception_v3