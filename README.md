[release-img]: https://img.shields.io/github/release/docer-savior/getter-setter-postfix-idea-plugin.svg
[latest-release]: https://github.com/docer-savior/getter-setter-postfix-idea-plugin/releases/latest
[plugin-img]: https://img.shields.io/badge/Idea%20Plugin-Setter%20Postfix%20Completion-orange.svg
[plugin]: https://plugins.jetbrains.com/plugin/19320
[jet-img]: https://img.shields.io/badge/plugin-Install%20Plugin-4597ff.svg
[jet]: http://localhost:63342/api/installPlugin?action=install&pluginId=gudqs7.github.io.getter-setter-postfix

[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT_CN.md)
[![license](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![GitHub release][release-img]][latest-release] 
[![Jetbrains Plugins][plugin-img]][plugin]
[![Version](http://phpstorm.espend.de/badge/19320/version)][plugin]  
[![Downloads](http://phpstorm.espend.de/badge/19320/downloads)][plugin]
[![Install Plugins][jet-img]][jet]  

---
[English ðºð¸](./README_EN.md)

# GenerateAllSetter Postfix Completion æ¯åä»ä¹çï¼

- æ¯ä¸ä¸ª IDEA æä»¶ï¼ä»æ¯æ Java ã
- åèäº GenerateAllSetter æä»¶ï¼ä½ä¸ºå¶è¡¥åï¼æ·»å äºå ä¸ª Postfix è¯­æ³ï¼åè½ä¸ GenerateAllSetter åºæ¬ä¸è´ã
- å¨ pojo åéä¹åéè¿ `.allset` çæææ setter
- å¨ pojo åéä¹åéè¿ `.allsetn` çæææè®¾ç½®å¨ï¼ä½æ²¡æé»è®¤å¼ï¼
- å¨ pojo åéä¹åéè¿ `.allget` çæææ getter
- å¨ä½¿ç¨ @lombok.Builder ç pojo åéä¹åéè¿ `.allbuilder` çæææ setter è°ç¨é¾

# ä¸ºä»ä¹è¿ä¸ªé¡¹ç®æç¨ï¼

- å¤ä¸ä¸ªéæ©ï¼å¦å¤æ¬äººè®¤ä¸º Postfix æ¯è¾é¡ºæï¼æå©äºè¿ä¸æ­¥æé«æçã
- ç»å¤§å®¶æä¾ä¸ä¸ª Postfix æä»¶å¼åæ¨¡æ¿ï¼å¸æå¤§å®¶å¤å¼åä¸äºæé«æççæä»¶ã

# æè¯¥å¦ä½å¼å§ï¼

## 1.å®è£æä»¶
### zip åå®è£
ä»ææ°ç [Release][latest-release] é¡µä¸è½½ zip åï¼ç¶åæå¼ IDEAï¼è¿å¥ Settings --> Plugins --> å°é½¿è½® --> Install Plugin from Disk  
![zip](parts/imgs/install-plugin-from-disk.png)

### Marketplace å®è£
æå¼ IDEAï¼è¿å¥ Settings --> Pluginsï¼éä¸­ Marketplaceï¼è¾å¥ GenerateAllSetter Postfix Completion ç¹å» Install  
![Marketplace](parts/imgs/install-from-marketplace.png)


## 2.æå¼ä¿ºæä¾çç¤ºä¾é¡¹ç®
ç¤ºä¾é¡¹ç®å°åï¼[docer-savior-plugin-usage-examples](https://github.com/docer-savior/docer-savior-plugin-usage-examples)  

æ  
```shell
git clone https://github.com/docer-savior/docer-savior-plugin-usage-examples
```
ä¸è½½åï¼æ¾å° `cn.gudqs.example.genset.GenerateSetterAndGetterUsage` æä»¶

## 3.æä»¶ä½¿ç¨

æ¼ç¤ºæä½¿ç¨çåºç¡ç±»  
```java

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

@Data
@Builder
@NoArgsConstructor
@AllArgsConstructor
class Foo {

    private Integer testInt;

    private Long testLong;

    private Float testFloat;

    private Double testDouble;

    private Boolean testBoolean;

}
```

### çæ set
```java
public void usage01() {
    // ç¨æ³1, çæææ set æ¹æ³, å¸¦é»è®¤å¼, éè¿ postfix
    Foo foo = new Foo();
    // åæ¶ä¸é¢çæ³¨é, åæ ä½äº allset åé¢, æä¸ Tab é®
//        foo.allset
    // å³å¯å¾å°ä¸é¢ç»æ, ä¸ foo.allset ä¼èªå¨æ¶å¤±
    foo.setTestInt(0);
    foo.setTestLong(0L);
    foo.setTestFloat(0f);
    foo.setTestDouble(0D);
    foo.setTestBoolean(false);
}
```

### çæ get
```java
public void usage03() {
    // ç¨æ³3, çæææ get æ¹æ³, éè¿ postfix
    Foo foo = new Foo();
    // åæ¶ä¸é¢çæ³¨é, åæ ä½äº allget åé¢, æä¸ Tab é®
//        foo.allget
    // å³å¯å¾å°ä¸é¢ç»æ, ä¸ foo.allget ä¼èªå¨æ¶å¤±
    Integer testInt = foo.getTestInt();
    Long testLong = foo.getTestLong();
    Float testFloat = foo.getTestFloat();
    Double testDouble = foo.getTestDouble();
    Boolean testBoolean = foo.getTestBoolean();
}
```


## Lombok ç @Builder å¿«éçæææèµå¼æ¹æ³çè°ç¨é¾

```java
public void usage04() {
    // ç¨æ³4, çæææ set æ¹æ³, éè¿ builder, éè¿ postfix
    // åæ¶ä¸é¢çæ³¨é, åæ ä½äº allbuilder åé¢, æä¸ Tab é®
//        Foo.builder().allbuilder
    // å³å¯å¾å°ä¸é¢ç»æ
    Foo foo = Foo.builder()
            .testInt(0)
            .testLong(0L)
            .testFloat(0f)
            .testDouble(0D)
            .testBoolean(false)
            .build();
}
```

## æ ¹æ®ä¸æ®µå«ææºå¯¹è±¡ï¼aï¼/ç®æ å¯¹è±¡ï¼bï¼ç b.setXxx(a.getXxx()) æ¹æ³ä»£ç çæææ set æ¹æ³ä»¥å¿«éå®ç°å¯¹è±¡è½¬æ¢

```java
public void usage05() {
    // ç¨æ³5, å° src çæ°æ®èµå¼ç» dest, å¸¸ç¨äºä¸¤ä¸ªä¸åç±»ç´æ¥è¿è¡ convert(éå­æ®µåç§°ç¸å), éè¿ postfix
    Foo src = new Foo();
    Foo dest = new Foo();
    // åæ¶ä¸é¢çæ³¨é, åæ ä½äº convert åé¢, æä¸ Tab é®
//        dest.setTestInt(src.getTestInt());.convert
    // å³å¯å¾å°ä¸é¢ç»æ
    dest.setTestInt(src.getTestInt());
    dest.setTestLong(src.getTestLong());
    dest.setTestFloat(src.getTestFloat());
    dest.setTestDouble(src.getTestDouble());
    dest.setTestBoolean(src.getTestBoolean());
}
```


# å¦æéè¦ï¼æå¯ä»¥ä»åªéè·å¾æ´å¤å¸®å©ï¼

## éè¿æäº¤ Issue æ¥è·åå¸®å©
 [ç¹å»è®¿é® Github Issue](https://github.com/docer-savior/getter-setter-postfix-idea-plugin/issues)  
> æ¬¢è¿å¤§å®¶æé®ï¼æ¬¢è¿å¤§å®¶ä¸èµ·å®åå®ï¼

**å¦å¤ï¼ææ¥å¥äº IDEA çéè¯¯å¤çç»ä»¶ï¼å æ­¤å½åç°æä»¶æ¥éæç¤ºæ¶ï¼æç§ IDEA æç¤ºï¼å¯æ¥çéè¯¯ä¿¡æ¯ï¼å¹¶ä¸é®ä¸æ¥ç»æï¼å³èªå¨çæä¸ä¸ª Issueï¼**

## éè¿æ¥ç Wiki æ¥è·åæ´å¤è¯´æ

- [å¥é¨æç¨](https://github.com/docer-savior/getter-setter-postfix-idea-plugin/wiki/%E5%85%A5%E9%97%A8%E6%95%99%E7%A8%8B)

## è´¡ç®æå
 [è´¡ç®æå](CONTRIBUTING_CN.md)

# è´è°¢åå

- [Github intellij-generateAllSetMethod](https://github.com/gejun123456/intellij-generateAllSetMethod)
- [Github genSets](https://github.com/yoke233/genSets)