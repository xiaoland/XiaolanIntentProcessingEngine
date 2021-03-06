# XiaolanIntentProcessingEngine
小蓝语义理解引擎

## 介绍：
- 小蓝语义理解引擎是一个开放的用于语音交互式机器人的一个语言理解引擎
- 小蓝语义理解引擎可以从用户的输入文本中分理出用户需要调用的技能里的意图和技能所需的槽位
- 当小蓝语义理解引擎无法处理时，将会通过讯飞语义理解引擎获得意图，但是这样将不能识别每个技能的特殊意图与槽位

## 使用方法：
- 调用Nlu.py文件中XiaolanNlu类里的start函数，参数有：1、文本
- 小蓝语义理解引擎需要一个意图列表（格式详见下面）用于为专门的机器人定制不同的体验
- 小蓝语义理解引擎的意图列表填写在Base.py里的Base类里的__init__函数里的intentlist变量里
- 小蓝语义理解引擎可以被clone下来，通过本地调用函数的方式使用，也可以通过HTTP请求调用（暂未开放）

## 小蓝语义理解引擎意图列表：
- 意图列表格式： （格式为python里的list）
- {
-     [intentname](总意图名称), [意图1, 意图2, 3, 4, ...](技能内意图), [[{'text': [(意图1用户表达式)]}, 'n': [(意图1用户表达式名词)], 'v': [(意图1用户表达式动词)], 'a': [(意图1用户表达式形容词)], 'r': [(意图1用户表达式介词)]](意图1的query), [(同上)](意图2的query)], [[意图1的槽位名称1， 意图一的槽位字典1(槽位字典介绍看下面)], [意图2的槽位名称2, 意图2的槽位字典2], ...](技能内槽位), skillname(技能名称)]
- }
- 槽位字典介绍与格式：（格式为python里的dict）
  - {
  -     'same_means': [],（同义词列表，与dict中的元素一一对应）
  -     'dict': []（主要字典，用途：例如：query为:明天早上叫我起床，槽位time的字典是time_dict，则就可以标注从query标注出“明天”）
  - }

