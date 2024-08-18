# Bilibili-Spider
B站“萝卜快跑“弹幕爬取+分析

一、项目背景
-------------
在互联网时代，用户生成内容（UGC）成为了研究社交行为和文化趋势的重要数据来源。B站（哔哩哔哩）作为一个主要的弹幕视频分享平台，聚集了大量的用户评论和互动数据。弹幕作为一种实时的用户反馈形式，具有即时性和高互动性的特点，为数据分析提供了丰富的素材。本项目旨在通过爬取B站上一个关于萝卜快跑无人驾驶汽车的视频弹幕数据，进行数据分析，挖掘用户的评论内容和行为模式。

二、项目目标
------------
* 弹幕数据爬取：使用Python编写爬虫程序，从指定视频中获取用户发布的弹幕数据。  
* 数据清洗与预处理：对爬取到的弹幕数据进行清洗和预处理，去除无效信息。  
* 数据分析：对弹幕数据进行词频统计、情感分析等，揭示用户的评论热点和情感倾向。  
* 结果可视化：通过词云图和情感分布图等可视化手段展示分析结果。    

三、项目文件
---------------
本项目包括以下主要文件：  
* danmu_crawler.py: 爬取弹幕数据的Python脚本。  
* data_cleaning.py: 数据清洗与预处理脚本。  
* word_frequency.py: 分词和词频统计脚本。  
* wordcloud.py: 生成词云图的脚本。  
* sentiment_analysis.py: 进行情感分析的脚本。  
* sentiment_distribution.py: 生成情感分布图的脚本。

四、使用说明
-----------------
环境配置：Python 3.8、pip install requests pandas jieba snownlp pyecharts  
安装必要的依赖库：requests、pandas、jieba、snownlp、pyecharts。

五、技术细节
----------------------
### （一）弹幕爬取 
#### 1、源码
运行 danmu_crawler.py 脚本，根据提示输入视频的oid、开始时间、结束时间和Cookie信息，爬取指定时间范围内（2024.07.01--2024.08.01）的视频弹幕数据并输出文件“danmaku.txt”。  
#### 2、结果
提取的弹幕内容:  
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/danmaku.png" width="680" height="150">
### （二）数据清洗
#### 1、源码
运行 data_cleaning.py 脚本，对爬取到的弹幕数据进行清洗，去除无效内容并保存为新的文本文件“clean-danmaku.txt”。  
#### 2、结果
数据清洗后的txt文件:  
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/clean_danmaku.png" width="680" height="150">
### （三）分词和词频统计
#### 1、源码
运行 word_frequency.py 脚本，对清洗后的弹幕数据进行分词和词频统计，并将结果保存输出为两个文件：分词后的文件“fenci-danmaku.txt”和词频统计文件“word_frequency_table.csv”。    
此脚本包括三部分任务：一是删除txt文件中的常用中文词比如那么、他们、不管等，以尽量消除对生成的词云图的影响。第二是对弹幕内容进行分词。第三是进行词频统计。  
* 停用词库：stopwords.txt
#### 2、结果
* 分词后的txt文件:
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/fenci-danmaku.png" width="680" height="150">
* 词频统计csv文件
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/word_frequency_table.png" width="280" height="350">

### （四）生成词云图  
#### 1、源码
运行 wordcloud.py 脚本，使用词频统计结果生成词云图并保存为HTML文件。  
#### 2、结果  
词云图:  
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/wordcloud.png" width="580" height="450">

#### 3、数据分析
通过对B站弹幕数据进行词频统计，我们可以获得用户在讨论萝卜快跑无人驾驶汽车视频时最常提到的词汇。这些词汇反映了用户关注的热点话题和主要观点。  
##### （1）词频统计分析详解  
###### ① 交通与职业相关
* 出租车（713次） ：作为讨论的主要对象，高频出现的“出租车”一词反映了用户对传统出租车行业的关注。用户可能在讨论无人驾驶技术如何影响现有的出租车服务，或者比较无人驾驶与传统出租车的优劣。  
* 司机（615次） ：与“无人驾驶”对比，用户可能在探讨司机职业的未来，讨论中包括担忧和期待，例如无人驾驶是否会完全取代人类司机，以及司机转型的可能性。  
* 网约车（425次） ：讨论无人驾驶技术对网约车行业的影响，用户可能在讨论无人驾驶网约车的优缺点，和传统网约车的对比。  
* 外卖（288次） ：这可能涉及无人驾驶在外卖配送中的应用，用户在探讨无人驾驶是否会应用于外卖行业，及其可能带来的影响。  
* 就业（144次） 、失业（192次） ：用户对无人驾驶技术对就业市场的影响表示担忧，特别是对驾驶员等相关岗位的失业问题。
###### ② 技术与公司
* 无人驾驶（551次） 、无人（283次） 、人工智能（80次） ：这些词汇表明用户对无人驾驶技术及其背后的AI技术有着浓厚的兴趣，讨论中可能包括技术原理、发展现状和未来前景。  
* 苹果（199次） 、特斯拉（197次） 、华为（69次） ：用户讨论不同科技公司在无人驾驶领域的进展和竞争。例如，苹果和特斯拉作为领先的科技公司，其在无人驾驶领域的成就和动向引起了广泛关注。
###### ③ 担忧与反对
* 没有（351次） 、问题（286次） 、不能（143次） ：用户对无人驾驶技术的现存问题和局限性进行了讨论，可能包括技术上的瓶颈、安全隐患和政策法规等方面的挑战。  
* 取代（258次） 、淘汰（118次） ：反映了用户对无人驾驶技术可能取代现有工作岗位的担忧。  
* 失业（192次） 、泡面（141次） ：可能是对失业问题的调侃，表达了对未来生活的不确定性和担忧。
###### ④ 前景与期望
* 需要（250次） 、进步（193次） 、发展（189次） 、市场（188次） ：用户讨论无人驾驶技术的发展需求和市场前景，可能包括对政策支持、技术创新和市场需求的讨论。  
* 便宜（173次） 、价格（96次） ：用户期待无人驾驶技术能够降低出行成本，提高运输服务的性价比。  
* 安全（91次） ：安全性是用户关注的重点，讨论中可能包括无人驾驶技术如何保证乘客和行人的安全。
###### ⑤ 情感与态度
* 可能（255次） 、真的（132次） 、完全（110次） ：用户对无人驾驶技术的可行性和可靠性进行了探讨，表达了各种观点。  
* 确实（178次） 、肯定（108次） 、支持（86次） ：一些用户对无人驾驶技术表示认可和支持，认为其未来具有广阔前景。  
* 根本（70次） 、不好（61次） ：部分用户对无人驾驶技术表示质疑和否定，认为其在某些方面存在不可逾越的障碍。
###### ⑥ 具体案例分析
* 偷换概念（153次） ：可能是用户在讨论中遇到的误导性言论或错误观点，并对此进行了反驳。例如，一些用户可能认为将无人驾驶与人类司机的优势进行对比时，存在偷换概念的现象。  
* 萝卜（153次） ：特指萝卜快跑这个品牌或技术，用户可能在讨论其在无人驾驶领域的应用和表现。  
* 滴滴（100次） ：作为网约车行业的代表，用户可能在讨论滴滴在无人驾驶技术中的表现和未来，或将其与其他无人驾驶技术进行比较。
###### ⑦ 地域与文化  
* 重庆（104次） ：讨论视频或弹幕中提到的特定城市，该城市在无人驾驶技术方面的进展。萝卜快跑首先在重庆运营，重庆作为中国西南地区的一个大城市，在无人驾驶技术的应用上有一些独特的实践和案例。  
* 中国（68次） 、美国（64次） ：讨论中涉及不同国家在无人驾驶技术领域的竞争和发展，用户可能在比较中美两国在该领域的技术水平和政策支持。
##### （2）总结
用户对无人驾驶技术的讨论涵盖了技术发展、就业影响、安全性、市场前景等多个方面。从高频词汇中可以看出，用户既有对新技术的期待和支持，也有对其潜在问题和负面影响的担忧。这些讨论反映了公众对无人驾驶技术的复杂态度和多元化观点。

### （五）情感分析/生成情感分布图
#### 1、源码
运行 sentiment_analysis.py 脚本和 sentiment_distribution.py 脚本，对弹幕数据进行情感分析，计算平均情感分数并保存分析结果，生成情感分布图并保存为HTML文件。  
#### 2、结果
* 每条弹幕的情感倾向：  
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/sentiment_analysis_results.png" width="280" height="350">
* 情感分布图：  
<img src="https://github.com/kexi3/Bilibili-Spider/blob/main/Inserted%20images/sentiment%20distribution.png" width="480" height="450">

#### 3、数据分析
##### （1）、数据
在我们爬取并分析的弹幕数据中，涉及到无人驾驶技术的视频评论具有丰富的情感表现。以下是弹幕的情感分类及其平均情感分数：  


##### （2）、情感分布与总体趋势
从情感分布来看，弹幕情感呈现多样化，但整体略偏向负面：  

* 负面情感（非常负面 + 负面）：3499条  
* 中性情感：1845条  
* 正面情感（正面 + 非常正面）：3261条  
平均情感分数为0.49，接近中性，但略偏负面。这表明用户对无人驾驶技术有较多的担忧和负面情绪，尽管也有不少正面的评价和期待。

##### （3）、负面情感分析
* 非常负面（1982条） ：高度负面的评论可能包含对无人驾驶技术的强烈批评和不满，反映出用户对技术的不信任或对其带来负面影响的强烈担忧。这些评论可能涉及到安全隐患、失业问题以及技术失败等。  
* 负面（1517条） ：负面评论则可能表达了用户的质疑和不安。例如，对无人驾驶技术的现状不满意，认为其在短期内难以成熟应用，或对其可能导致的社会问题表示担忧。
##### （4）、中性情感分析
* 中性（1845条） ：中性的评论往往是描述性和客观性的，用户可能在讨论无人驾驶技术的现状、原理、具体应用等，而不带有明显的情感倾向。这些评论对了解用户的理性分析和中立观点非常有价值。
##### （5）、正面情感分析
* 正面（1423条） ：正面评论反映了用户对无人驾驶技术的认可和期待。用户可能赞赏技术的先进性、对未来生活的便利性及其在解决当前交通问题上的潜力。  
* 非常正面（1838条） ：高度正面的评论可能表达了用户的强烈支持和乐观态度。例如，认为无人驾驶技术将带来革命性的变化，彻底改变交通和出行方式，提高生活质量。
##### （6）、具体情感案例
结合词频统计数据，可以更深入地理解用户情感：  

* 担忧与批评：高频出现的“问题”、“不能”、“取代”、“失业”、“泡面”等词汇与负面情感相关，用户对无人驾驶技术可能带来的社会问题和技术不成熟表示担忧和批评。  
* 中立讨论：词汇如“现在”、“技术”、“市场”、“价格”等，与中性情感相关，用户在进行客观的技术讨论和市场分析。  
* 支持与期待：高频出现的“进步”、“发展”、“便宜”、“安全”等词汇，与正面情感相关，用户对无人驾驶技术的进步、安全性和未来应用充满期待和支持。
##### （7）、总结
通过情感分析，可以看出用户对无人驾驶技术的态度复杂且多样。尽管整体情感略偏负面，但中立和正面的评论也占据了很大比例。负面情感主要源自对技术不成熟、潜在安全问题及其对就业市场影响的担忧。而正面情感则集中在对技术进步的认可和对未来便利生活的期待。  
这种情感分布反映了无人驾驶技术作为一项前沿技术，既带来了巨大的发展潜力，也引发了广泛的社会讨论和情感波动。对于相关企业和研究机构，这些情感分析提供了宝贵的用户反馈，有助于了解公众的关注点和疑虑，从而更好地推进技术研发和市场推广。




