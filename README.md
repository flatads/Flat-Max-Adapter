# Flat-Max-Adapter

## 发版记录

| 版本       | 发布时间       | 更新内容    |
|----------|------------|---------|
| 1.4.18.2 | 2024-02-23 | 发布第一个版本 |

## 引入Adapter

首先在项目级build.gradle文件加入maven远程依赖地址，如下：
```groovy
buildscript {
    repositories {
        maven { url "https://maven-pub.flat-ads.com/repository/maven-public/"}
        maven { url "https://jitpack.io" }
    }
}
allprojects {
    repositories {
        maven { url "https://maven-pub.flat-ads.com/repository/maven-public/"}
        maven { url "https://jitpack.io" }
    }
}

```
然后再Module的build.gradle中引入Max Adapter的包，根据项目情况选择
```groovy
// 必须导入
implementation 'com.flatads.adapter:max:1.4.18.2'

// 以下按渠道导入
// GP
implementation 'com.flatads.sdk:flatads:1.4.18.2-GP'

// 线下
implementation 'com.flatads.sdk:flatads:1.4.18.2'

```
## 在Max用户界面中定义Adapter

1. **创建NetWork类名：
com.flatads.adapter.max.FlatAdsMediationAdapter**

2. **配置广告位ID**
   * 在 *Placement ID* 输入FlatAds配置好的广告位ID，如：`6af5ffa0-bb5e-11ed-af5d-07a5f3732048`
   * 在 *Custom Parameters* 输入FlatAds后台申请好的 app_id 和 app_token，使用Json格式输入，如：`{ "app_id":"YOUR_APP_ID" , "app_token":"YUOR_APP_TOKEN" }`

3. 以上配置完成后，点击保存即可。注意：生效时间，需要等待30~60分钟左右。

#### 注意事项：
1. Banner 广告，需要在 BannerView回调`onAdLoaded`时候再添加在布局上，否则Max会触发两次Banner加载，导致广告无效请求。




