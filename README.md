<div align="center">
<h1>AdGuard Rule</h1>
  <p>
    一个简易的Java程序，用于合并与更新 AdGuard Home 过滤规则
</p>
</div>

<p><a href="https://raw.githubusercontent.com/QING23qin/AdGuardHome-Rule/main/rule/adgh.txt">AdGuardHome Filter</a></p>
<p><a href="https://mirror.ghproxy.com/https://raw.githubusercontent.com/QING23qin/AdGuardHome-Rule/main/rule/adgh.txt">AdGuardHome Filter国内镜像1</a></p>
<p><a href="https://down.npee.cn/?https://raw.githubusercontent.com/QING23qin/AdGuardHome-Rule/main/rule/adgh.txt">AdGuardHome Filter国内镜像2</a></p>


<h2 id="a">📔 说明</h2>

本项目旨在按需求整合 `AdGuard` 规则。定时从上游订阅获取规则，去除`重复`和`不受支持`的规则并进行分类。如果存在误杀请手动放行。  
支持`AdGuard Home`,每`12小时`自动更新一次   

#### 上游规则

<details>
<summary>点击查看</summary>
<ul>
    <li><a href="https://adaway.org/hosts.txt">AdAway Default Blocklist</a></li>
    <li><a href="https://raw.githubusercontent.com/E7KMbb/AD-hosts/master/system/etc/hosts">E7KMbb Ad-host</a></li>
    <li><a href="https://easylist-downloads.adblockplus.org/easylistchina.txt">Easylist China</a></li>
    <li><a href="https://raw.githubusercontent.com/Lynricsy/HyperADRules/master/dns.txt">HyperADRules</a></li>
    <li><a href="https://raw.githubusercontent.com/lingeringsound/10007_auto/master/all">10007_auto</a></li>
    <li><a href="https://raw.githubusercontent.com/privacy-protection-tools/anti-AD/master/anti-ad-easylist.txt">anti-ad</a></li>
    <li><a href="https://raw.githubusercontent.com/TG-Twilight/AWAvenue-Ads-Rule/main/AWAvenue-Ads-Rule.txt">秋风广告规则,针对Android广告</a></li>
    <li><a href="https://raw.githubusercontent.com/jdlingyu/ad-wars/master/hosts">大圣净化</a></li>
    <li><a href="https://raw.githubusercontent.com/zsakvo/AdGuard-Custom-Rule/master/rule/zhihu.txt">知乎 普通版</a></li>
    <li><a href="https://raw.githubusercontent.com/Cats-Team/AdRules/main/dns.txt">杏稍AdRules DNS List</a></li>
    <li><a href="https://adguardteam.github.io/HostlistsRegistry/assets/filter_29.txt">adguard中文/a></li>
    <li><a href="https://raw.githubusercontent.com/xinggsf/Adblock-Plus-Rule/master/rule.txt">乘风 广告过滤规则</a></li>
    <li><a href="https://raw.githubusercontent.com/xinggsf/Adblock-Plus-Rule/master/mv.txt">乘风 视频过滤规则</a></li
                                                                                                           
    # 本地列表
    <li><a href="https://raw.githubusercontent.com/QING23qin/AdGuardHome-Rule/main/rule/mylist.txt">mylist</a></li>
    <li><a href="https://raw.githubusercontent.com/QING23qin/AdGuardHome-Rule/main/rule/yyy.txt">yyy（来自urkbio的AdGuard-Rule）</a></li>
      <li><a href="https://raw.githubusercontent.com/QING23qin/AdGuardHome-Rule/main/rule/oldhost.txt">oldhost</a></li>
</ul>
</details>


#### 示例配置

```yaml
application:
  rule:       
    #远程规则订阅，仅支持http、https
    remote:
      - 'https://example.com/list.txt'
    #本地规则，请将文件移动到项目路径rule目录中
    local: 
      - 'mylist.txt'
  output:
    path: rule   #规则文件输出路径，相对路径默认从 项目目录开始
    files:
      all.txt:    #输出文件名
        - DOMAIN  #域名规则，仅完整域名
        - REGEX   #正则规则，包含正则的域名规则，AdGH支持
        - MODIFY  #修饰规则，添加了一些修饰符号的规则，AdG支持
        - HOSTS   #Hosts规则
```

#### 使用 Github Action

- fork本项目
- 参照示例配置，修改配置文件: `src/main/resources/application.yml`，注意本地规则文件应放入项目根目录 `rule` 文件夹
- 编辑 `.github/workflows/auto-update.yml` 文件，将 `Commit Changes` 区块下邮箱与用户名修改为自己的（Github邮箱与用户名）
- 提交所有修改并等待 `Github Action` 执行，执行完成后相应规则生成在配置中指定的目录下


- 👉 特别感谢@fordes123



