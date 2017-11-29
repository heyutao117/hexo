---
layout: layout
title: iOS代码重构的感悟
date: 2017-11-28 17:21:15
tags:
---
<p>先交代下背景吧，最近领导安排接手一个第三方公司开发的老项目，代码风格就不说了，反正里面的坑太多了，下面我将详细介绍下项目中的坑和编写代码应该注意或者必须的规范。</p>

<h3>命名规范真的很重要</h3>
<p>按照下面这个命名方式,估计很少人能够根据方面名判断这是干啥的吧。</p>

```
- (void)sendDict9999999999:(NSString *)string
```
<h3>代码封装有问题</h3>
<p>作为一个工具类，如果把业务逻辑都放在工具类里面，那么代码的耦合性太强了</p>
```
-(void)locationManager:(CLLocationManager *)manager didUpdateLocations:(NSArray<CLLocation *> *)locations
```
<h3>宏定义乱用</h3>
<p>#ifdef + condition 但是这个condition就是一个没有赋值的宏定义，怎么着都进不了if里面的逻辑
</p>
```
#ifdef TIMER_METHOD
    [kUserDefaults removeObjectForKey:@"lastLocation"];
    [kUserDefaults synchronize];
#endif
```
<h3>代码该删的不删，会导致可读性下降</h3>
<p>也许是个老工程，经过多次迭代遗留下大把废弃的方法，很多方法没有被工程的类或者方法引用，但是仍在存在于工程的各个角落，导致代码的可读性很差</p>
```
- (void)judgeIfNeedDownloadHtml
```
<p>这个方法工程里面都被别的类或者方法没有引用，围绕这个方法衍生一堆的逻辑，导致工程很臃肿,代码还是该删的就删，不要瞻前顾后</p>
<h3>单例里面重新dealloc，添加各种逻辑</h3>

```
- (void)dealloc
{
    [self setSearchDelegateNil];
    
    [[NSNotificationCenter defaultCenter] removeObserver:self];
    [[LocationTool sharedInstance] setSearchDelegateNil];
}
```
<p>单例在APP的生命周期之内都不会被释放的，为啥各种逻辑写在deallo里面去呢</p>
<h3>类名命名不规范类名命名不规范</h3>
<p>有些类的前缀是 CY 或者 YD不统一,看起来很乱</p>


