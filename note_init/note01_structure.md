mmdetection 中最大的特点是注册器机制

## 理解 Registry
其有两种方法：
- 定义一个类，在类上方采用@xx.register_module()方式进行注册
```python
backbones = Registry("backone")
@backones.register_module()
class ResNet:
    pass

```
- 直接注册自己实现或者任何地方已经实现的类到注册器中
```python
ACTIVATION_LAYERS.register_module(module=nn.ReLu)
```
一旦注册进去，那么配置里就可以通过dict(type='类名', 类参数) 方式实例化指定类

**特点：扩展性非常强，解耦性也很好**
> 其核心原理就是简单的装饰器。Registry类把python装饰器功能封装为了类，原因是类可以存储实例对象。真正起作用的还是装饰器函数register_module，其返回一个装饰器函数。

“Registry类把python装饰器功能封装为了类”，装饰器封装成类是怎么实现的？

```python 
```

### 参考
[知乎-mmdetection最小复刻版(一)：整体概览](https://zhuanlan.zhihu.com/p/252616317)