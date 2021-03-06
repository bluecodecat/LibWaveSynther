# LibWaveSynther

上古神器 II : 可编程软波表音频发生器

曾几何时, 我们问道: “难道, 单片机发出的声音, 只能是单调的蜂鸣器滴滴响么……?”

**绝! 对! 不! 是!**

这个项目只需消耗你的少量CPU和内存资源, 还你一个如同YM2413等MIDI音频合成芯片的高级音质!

做提示音丰富的软件? 做游戏? 跑音效轨? 都不是问题!

**注意: 该项目因涉及大量整型运算优化, 需要32位机方可运行**

**请放弃手里的51单片机吧, 建议使用STM32/ESP8266/ESP32等更加先进且便宜的设备来运行**

# 它可以做什么?

 - 多通道88键音频发生器, 每个通道可同时产生一个音符
 
 - 不限制最高通道数量, 如果你想, 那就直到用光所有CPU资源为止!
 
 - 双缓冲设计, 无惧短暂的CPU抢占或突发音符
 
 - 16位音质高质量渲染, 时代变了, 让我们和8bit说再见!
 
 - ADSR(按下、衰减、保持、释放)包络支持! 轻松打造吹奏乐器和弹奏乐器等不同乐器风格!
 
 - 算法无除法和浮点, 极限优化, 在STM32F103C6T6(64MHz HSI)环境下能够稳定6通道44100Hz输出或15通道28000Hz输出
 
 - 每个声道都可以定义一个不同的音色(512长度16bit带符号波表)
 
 - 你想不到的内存占用, 最小可以小到不足2KB!
 
 - 你甚至可以使用这个来当音效发生器!
 
 - 项目甚至提供了将MIDI文件直接转换格式的Python脚本, 以及各种各样需要用到的其他代码生成脚本……

# 所以这又是个什么黑科技?

这个库源于一个非常古老的技术 —— 软波表合成器技术, 在早期的PC游戏、FC游戏机、SFC游戏机、GBA游戏机等曾经被大规模应用.

后随着时间的流逝和技术的发展, 这项技术逐渐被丰富的空余资源和更高的处理器性能所遗忘.

如今这项技术就像是消失在了互联网上, 几乎再也找不到它的影子了. 更有很多人听都没听说过这种音频合成技术.

这个项目就是想将这一种古老而高效的技术保存下来, 让大家重新有机会能够学习到这种技术 —— 原来只有几个波形也可以合成一个完整的音乐!

# 所以能给我讲讲它的原理么?

当然可以!

一首完整的音乐, 虽然可以被直接录制下来, 然后播放 —— 但是这样就占用了非常多的存储资源来将整首曲子完整记录.

即使是被MP3格式压缩过的音乐文件, 也是大部分都要MB级别. 这显然是我们无法接受的.

那么…… 如果将曲谱记录下来, 在CPU运行的时候, 动态弹奏生成…… 岂不是能够节省下大量资源么?

这就是这项技术的全部原理.

我们只要得到一个简单的波表, 并将其按照一定的频率不断的循环播放, 加上音量控制(包络), 就能做出一些基本的乐器来.

之后改变这个播放的频率, 就能还原钢琴的整个88键音域 —— 这就是这个项目的全部工作啦!

这样的计算并不复杂, 所以这个算法高效且可行, 且并不难实现.

# 所以有没有Example代码呢?

目前已经提供x86版本(Windows下DirectSound接口输出)的Example代码和exe文件.

STM32版本正在整理, 大家莫急.

# Demo中用到的曲子是什么?

东方Project的《恋娘 ～湖上ノ旋律～》.

# 所以最后, 开源许可证呢?
MIT License, 代码无任何担保. 不过, 如果你发现了什么BUG, 欢迎提出issue或者开pull request.
