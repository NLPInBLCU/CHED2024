# CCL2024-Eval 古文历史事件类型抽取评测任务（CHED2024）

* 主办单位：北京语言大学-信息科学学院-语言文化计算研究室
* 组织者：邵艳秋，李炜
* 负责人及联系方式：冯振冰blcu_lcclab@163.com
* 联系人及联系方式：冯振冰blcu_lcclab@163.com

## 一、任务内容

### 1. 任务背景

事件抽取是从自然语言文本中识别和提取相关事件信息的过程。由于古文句法、语义复杂，使用范围小，针对古代汉语的信息抽取任务仍然面临着较大挑战。我们构建了古代汉语事件类型体系，并基于《二十四史》语料构建了中国古文历史事件检测数据集CHED[1]，我们构建的事件类型体系一共包含9大类、67小类，共标注了8122个有效事件实例（包括触发词和事件类型），相关论文已在CCL2023上发表。为了进一步推动古代文本事件抽取任务的研究，我们依托CCL2024推出古文历史事件类型抽取评测任务，旨在为研究者提供学术交流平台，进一步提升事件抽取技术及中国古代历史文本的数字化研究水平。

### 2. 任务定义

任务旨在评估古文历史事件检测的算法性能，包括两个子任务：

#### 子任务一：触发词识别（Trigger Identification）

此任务需要识别文本中的事件触发词并标记它们的位置。触发词为最能代表事件发生的词语，一般为句中的谓语动词（其他句子成分皆可）。我们构建的数据集采用最简触发词原则[1]，触发词以单音节词为主。

#### 子任务二：事件类型判别（Event Type Classification）                                                               
我们构建了一个具有层级逻辑性的事件类型体系（见Classical Chinese Historical Event Schema.jsonl），此任务需要参考给定的事件类型体系，为每个触发词确定其所属的事件类型。

<div align=center>
<img width="211" alt="image" src="https://github.com/NLPInBLCU/CHED2024/assets/45780284/e64f13b7-c966-43d7-9c86-37e265b58f0f">
</div>

举例来说，在句子“进军建德，擒贼帅赵桑干。”中，“进军”这个词可以表示“派兵到建德”这个事件，“擒”这个词可以表示“抓住敌方的将领赵桑干”这个事件。因此在这个句子中，触发词是“进军”和“擒”，分别代表“军事-备战-出兵”和“军事-作战-俘虏”这两个事件类型。

### 3.事件类型体系

![schema](https://github.com/NLPInBLCU/CHED2024/assets/45780284/d03f4c4e-bbcf-4859-a47e-aaf093d94cec)

详见 Schema 文件：[Classical Chinese Historical Event Schema.jsonl](https://github.com/NLPInBLCU/CHED2024/blob/main/Classical%20Chinese%20Historical%20Event%20Schema.jsonl)

## 二、 评测数据
我们从《二十四史》中选取了13159句语料进行标注，最后构建出了包含8122个有效事件实例的数据集CHED，各史书以及训练集、验证集、测试集的数据分布如下表所示：

| 史书 | 训练集  | 验证集  | 测试集  | 总计   |
|----|------|------|------|------|
| 1  | 史记   | 521  | 96   | 98   | 715  |
| 2  | 三国志  | 343  | 86   | 66   | 495  |
| 3  | 周书   | 483  | 118  | 113  | 714  |
| 4  | 梁书   | 38   | 7    | 14   | 59   |
| 5  | 魏书   | 174  | 32   | 24   | 230  |
| 6  | 后汉书  | 281  | 58   | 61   | 400  |
| 7  | 宋书   | 75   | 10   | 24   | 109  |
| 8  | 南齐书  | 81   | 21   | 30   | 132  |
| 9  | 汉书   | 417  | 100  | 81   | 598  |
| 10 | 晋书   | 236  | 44   | 44   | 324  |
| 11 | 陈书   | 101  | 21   | 27   | 149  |
| 12 | 北齐书  | 141  | 27   | 21   | 189  |
| 13 | 明史   | 249  | 42   | 47   | 338  |
| 14 | 南史   | 238  | 52   | 68   | 358  |
| 15 | 隋书   | 205  | 43   | 37   | 285  |
| 16 | 新五代史 | 528  | 117  | 123  | 768  |
| 17 | 宋史   | 302  | 49   | 67   | 418  |
| 18 | 北史   | 227  | 60   | 49   | 336  |
| 19 | 新唐书  | 70   | 25   | 33   | 128  |
| 20 | 旧唐书  | 175  | 51   | 49   | 275  |
| 21 | 辽史   | 98   | 18   | 14   | 130  |
| 22 | 元史   | 271  | 68   | 78   | 417  |
| 23 | 金史   | 175  | 32   | 36   | 243  |
| 24 | 旧五代史 | 221  | 41   | 50   | 312  |
|    |      | 5650 | 1218 | 1254 | 8122 |

## 三、评价标准

参赛者在测试集上参与评测。

### 子任务一：触发词识别（得分占整个任务40%）

参赛者需提交一个包含每个句子中触发词的位置信息的结果文件。

| 评价指标 | BLEU（2-gram）                           |
|------|----------------------------------------|
|      | ROUGE（2-gram）                          |
|      | Exact-match-score                      |
| 总分计算 | （BLEU + ROUGE + Exact-match-score）/ 3​ |

### 子任务二：事件类型判别（得分占整个任务60%）

参赛者需提交一个包含每个触发词及其预测的事件类型的结果文件。我们构建的事件类型体系一共包含9大类、67小类，子任务二被分为粗粒度（9大类）和细粒度（67小类），并使用宏平均（macro-average）和微平均（micro-average）两个指标进行评估。

| 宏平均  | Macro Precision = Σ (每个大/小类的精确度)  / （大/小类的总数9/67） |
|------|---------------------------------------------------|
|      | Macro Recall = Σ (每个大/小类的召回率)  / （大/小类的总数9/67）    |
|      | Macro F1 = Σ (每个大/小类的 F1 值)  / （大/小类的总数9/67）      |
|      |
| 微平均  | Micro Precision =所有实例的正确判别数量 / 所有实例的判别数量          |
|      | Micro Recall =所有实例的正确判别数量 / 所有可能的实例数量             |
|      | Micro F1 =（2 * Mi F1 * Mi R） /  (Mi F1 + Mi R)    |
| 总分计算 | （Macro F1 + Micro F1）/ 2                          |

### 综合评价标准

0.4 * 任务一得分 + 0.3 * 任务二粗粒度得分 + 0.3 * 任务二细粒度得分

## 四、参考文献
[1] Wei Congcong, Feng Zhenbing, Huang Shutan, Li Wei, and Shao Yanqiu. 2023. CHED: A Cross-Historical Dataset with a Logical Event Schema for Classical Chinese Event Detection. In Proceedings of the 22nd Chinese National Conference on Computational Linguistics, pages 875–888, Harbin, China. Chinese Information Processing Society of China.

[2] Feng Yao, Chaojun Xiao, Xiaozhi Wang, Zhiyuan Liu, Lei Hou, Cunchao Tu, Juanzi Li, Yun Liu, Weixing Shen, and Maosong Sun. 2022. LEVEN: A Large-Scale Chinese Legal Event Detection Dataset. In Findings of the Association for Computational Linguistics: ACL 2022, pages 183–201, Dublin, Ireland. Association for Computational Linguistics.

[3] Xiaozhi Wang, Ziqi Wang, Xu Han, Wangyi Jiang, Rong Han, Zhiyuan Liu, Juanzi Li, Peng Li, Yankai Lin, and Jie Zhou. 2020. MAVEN: A Massive General Domain Event Detection Dataset. In Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), pages 1652–1671, Online. Association for Computational Linguistics.

[4] Doddington, G. R., Mitchell, A., Przybocki, M. A., Ramshaw, L. A., Strassel, S. M., & Weischedel, R. M. (2004, May). The automatic content extraction (ace) program-tasks, data, and evaluation. In Lrec (Vol. 2, No. 1, pp. 837-840).

[5] Jacqueline Aguilar, Charley Beller, Paul McNamee, Benjamin Van Durme, Stephanie Strassel, Zhiyi Song, and Joe Ellis. 2014. A Comparison of the Events and Relations Across ACE, ERE, TAC-KBP, and FrameNet Annotation Standards. In Proceedings of the Second Workshop on EVENTS: Definition, Detection, Coreference, and Representation, pages 45–53, Baltimore, Maryland, USA. Association for Computational Linguistics.

[6] Q. Li et al., "A Survey on Deep Learning Event Extraction: Approaches and Applications," in IEEE Transactions on Neural Networks and Learning Systems, 2022, doi: 10.1109/TNNLS.2022.3213168.

[7] Jacob Devlin, Ming-Wei Chang, Kenton Lee, and Kristina Toutanova. 2019. BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding. In Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers), pages 4171–4186, Minneapolis, Minnesota. Association for Computational Linguistics.

[8] Sepp Hochreiter, Jürgen Schmidhuber; Long Short-Term Memory. Neural Comput 1997; 9 (8): 1735–1780. doi: https://doi.org/10.1162/neco.1997.9.8.1735

[9] Y. Cao and A. Yusup, "Chinese Electronic Medical Record Named Entity Recognition based on BERT-WWM-IDCNN-CRF," 2022 9th International Conference on Dependable Systems and Their Applications (DSA), Wulumuqi, China, 2022, pp. 582-589, doi: 10.1109/DSA56465.2022.00084.

