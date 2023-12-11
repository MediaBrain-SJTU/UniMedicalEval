
# UniMedicalEval
我们提出了一个医疗大语言模型的综合评测框架，具有以下三大特点：

**大规模数据集的综合分析能力**：UniMedicalEval拥有超过100,000个高质量数据样本，覆盖医疗AI领域的多个细分场景，从基础诊断到复杂病理学分析。这一大数据量的处理能力不仅证明了其在数据集成和多维度分析方面的能力，而且反映UniMedicalEval在复杂医疗情境中应用的前沿性。

**经过验证的临床数据真实性**：UniMedicalEval使用的55,000例真实病例数据，均经过医疗专家的验证和筛选，确保了数据集的高度真实性和临床相关性。这种严格的数据质量管理，使得UniMedicalEval能够在评估医疗模型的临床适用性和决策精度方面提供权威的参考标准。

**异构数据集的高效处理与分析**：UniMedicalEval能够处理包括病历记录、检验报告、医嘱和手术记录在内的多种异构数据类型，并在这些不同数据类型间进行有效的关联分析。这种能力不仅体现了模型在处理和解析医疗信息的复杂性方面的能力，也展示了其在提供跨数据源综合性医疗洞察方面的领先地位。

## 1：数据集

## 1.1 数据集生成Pipeline

<p align="center">
  <img src=class/pipeline.png width=600px/>
</p>

- 数据收集：从网络上，医学考试题，医院的患者信息中收集原始数据。

- 数据清洗：对原始数据进行清洗和匿名化处理。数据清洗包括去掉患者病历中书写质量较差的，比较模板化回复缺乏实质信息，存在书写错误的病程记录等等。同时，我们还对医院中的化验单数据和影像学检查报告进行清洗。数据清洗的目的是确保清洗后的多种数据格式间有较为清晰的对应关系，尽量减少数据集中的噪声。
  
- 医生校验：专业医生从实用性，可靠性的角度对评估数据集进行校验。数据集校验的部分主要在于判断当前评估场景是否存在实际应用价值，是否是行之有效的医学问题以及是否与专业医生的逻辑思维关系相符合。专业医生校验的目的是为了让评估数据集能够符合人类医生的思维方式，有实际的应用价值和清晰的逻辑关系。

- 场景划分：通过与专业医生讨论，根据面向患者/面向医生对不同维度下的不同场景进行了划分，明确至六大维度20个精细化医疗场景，并对应的对评测数据集进行划分。
  
- 提问优化：由专业医生给出不同场景下需要思考与研究的问题，使评测数据集中的提问更专业与复杂。
  
- 调整格式：利用GPT-4将评测数据集构建成选择题与生成式格式便于评估。




## 1.2 数据集信息介绍
UniMedicalEval数据集的分布格式如下：

##  1.2.1 数据分布

<p align="center">
  <img src=class/data4.png width=900px/>  
</p>


-数据分析：UniMedicalEval的数据集涵盖了6大医疗领域的任务和20种精细化医疗情境，具体数据分布如下表所示：


|评测维度|	医疗场景|	数据量|	
|------|------------|-----------------|
|案例分析	|疾病诊断	|17,832	|
|案例分析|	诊断依据|	1,320	|
|案例分析|	医嘱建议	|6,420|	
|案例分析|	手术方案建议|	1,100	|
|案例分析|	风险咨询	|2,500	|
|知识问答|	疾病介绍	|2,000	|
|知识问答|	手术咨询|	800	|
|知识问答|	基础医疗问答|	12,000	|
|报告解读|	异常解读|	5,000	|
|报告解读|	化验项目选择|	5278	|
|报告解读|	报告诊断|	11,000|	
|报告解读|	检查推荐	|11,000	|
|报告解读|	治疗咨询	|8,000	|
|信息整合|	病历概要	|1,500	|
|信息整合|	术前信息整理|	1,500|	
|便捷问诊|	预问诊|	10,000	|
|便捷问诊|	快速问诊	|10,000	|
|情景对话|	在线问诊	|5,000|	
|情景对话|	医疗反事实|	10,000	|
|情景对话	|毒害伦理|	2,000	|



## 1.2.2 细分医疗场景介绍

我们在下面详细介绍了我们的六大维度与二十种细分医疗场景。在每个细分场景的超链接中我们给出了数据集示例和介绍。

**维度一：案例分析**

[疾病诊断](class/疾病诊断.md)，诊断依据，医嘱建议，手术方案建议，风险咨询

**维度二：知识问答**

疾病介绍，手术咨询，[基础医疗问答](class/基础医疗问答.md)

**维度三：报告解读**

异常解读，化验项目选择，[报告诊断](class/diseasecheck.md)，[检查推荐](class/检查推荐.md)，[治疗咨询](class/治疗咨询.md)

**维度四：信息整合**

病历概要，术前信息整理

**维度五：便捷问诊**

[预问诊](class/预问诊.md)，快速问诊

**维度六：情景对话**

在线问诊，[医疗反事实](class/医疗反事实.md)，毒害伦理

## 2. 评测指标

UniMedicalEval的评测方式分为选择题评测和生成式评测两种。选择题评测的内容如下：


## 2.1. 选择题评测

**🥇 Leaderboard**

更多结果请查看 [Leaderboard](class/leaderboard1.md).

| 模型| 疾病诊断 | 基础医疗问答| 报告诊断| 检查推荐| 治疗咨询| 预问诊 | 医疗反事实| 手术规划| 检查项目选择 |Avg|
|------|------------|-----------------|-----------------|------|------|------|------|------|------|------|
|GPT-4|0.79|0.72| 0.96|0.94|0.81|--|0.89|0.74|0.72|--|
|文心一言|0.63|0.60| 0.89|0.86|0.68|0.42|0.74|0.67|0.87|0.71|
|Huatuo2-13B|0.58|0.51| 0.96|0.94|0.65|--|0.57|--|--|--|
|通义千问|0.50|0.49|0.91|0.89|0.64|0.35|0.40|0.57|0.86|0.62|
|星火|0.45|0.47|0.87|0.80|0.57|0.40|0.39|--|--|--|
|Baichuan-chat-13B|0.27|0.24|0.63|0.32|0.29|--|0.48|--|--|--|
|InternLM-7B|0.25|0.22|0.15|0.07|0.18|--|0.47|--|--|--|

实验结论

-综合来看，GPT-4仍然是最强大的通用模型，但是在有的场景下表现会劣于Huatuo2-13B和文心一言

-文心一言和GPT-4达到了相近的性能，在大部分场景中都有不错的性能

-Huatuo2-13B是性能非常优异的领域小模型，超过了通义千问和星火大模型的表现，在部分场景下能达到与GPT-4接近的性能

-有的模型在处理如医疗反事实等场景时表现不佳，容易出现过于自信的现象而回答所有问题，无论问题本身是否可以回答。






## 2.2 生成式评测

我们收集了[手术操作](https://github.com/MediaBrain-SJTU/UniCMedEval/blob/main/%E6%89%8B%E6%9C%AF%E6%93%8D%E4%BD%9C%E6%9C%AF%E8%AF%AD.xlsx)，[疾病诊断](https://github.com/MediaBrain-SJTU/UniCMedEval/blob/main/%E7%96%BE%E7%97%85%E8%AF%8A%E6%96%AD%E6%9C%AF%E8%AF%AD.xlsx)，[医疗操作](https://github.com/MediaBrain-SJTU/UniCMedEval/blob/main/%E5%8C%BB%E7%96%97%E6%93%8D%E4%BD%9C%E6%9C%AF%E8%AF%AD.xlsx)三个术语库以进行我们的生成式评测。

我们的生成式评测分为结构化回复抽取和术语对齐两个部分。

**结构化回复抽取**

```json
{ "original_output": "根据患者的症状、体征和检查结果，可以初步考虑以下疾病诊断和治疗建议：舌根新生物：患者主要症状是舌根处的新生物，可能需要进一步的检查以明确性质，例如切除组织并进行病理学检查。这有可能是良性病变，也可能是恶性肿瘤，所以需要进一步评估。慢性咽炎：患者有慢性咽炎的病史，这可能导致咽部不适和咳嗽咳痰。治疗建议包括喉咙保湿、避免刺激物质、遵医嘱使用抗炎药物或抗生素来缓解症状。Brugada波样改变：心电图显示Brugada波样改变，这可能与心脏的电传导异常有关。这需要进一步的心脏评估，包括心脏超声、心脏电生理检查等。治疗建议将根据进一步评估的结果而定，可能包括药物治疗或其他干预措施。",
    "structured_output": "疾病诊断：舌根新生物，慢性咽炎 治疗建议：喉咙保湿、使用抗炎药物或抗生素、心脏超声",
},
```
- original_output: 待测模型的原本输出
- structured_output：将待测模型的原本输出转化为结构化字典格式。此步骤通过在我们部分评测数据集上finetune的Baichuan-chat-13B完成

**术语对齐**
<p align="center">
  <img src=class/术语对齐.png width=800px/>
</p>


利用上述医学标准化术语库对结构化字典回复中的value与答案的相似度。


**生成式评测指标**
- Precision：结构化回复中字典的key与GT的key计算precision
- Recall：结构化回复中字典的key与GT的key计算Recall
- Bert score：结构化回复中字典的value与术语库对齐后与GT计算Bert score


## 🪶贡献

本项目由上海人工智能实验室、上海交通大学和华东师范大学合作完成。联合研发团队由王延峰教授领衔，成员包括[张娅](https://mediabrain.sjtu.edu.cn/yazhang/)教授、[王钰](https://mediabrain.sjtu.edu.cn/yuwang/)副教授、[王琳琳](https://faculty.ecnu.edu.cn/_s16/wll/main.psp)研究员，李然，贺樑，欧阳泽田，邱易帅，蔡琰，张燮驰，杨宇辰，廖育生，郭逸秋等。与本项目相关的论文有(https://arxiv.org/pdf/2309.02077v1.pdf)。



## 道德规范声明

本评测数据集使用的所有数据均已通过医院道德规范审查，保证了匿名性和安全性。


## 引用

@misc{MedEvalHub,
  author={Yan Cai, Linlin Wang,Ye Wang, Gerard de Melo, Ya Zhang, Yan-Feng Wang, Liang He}, 
  title = {MedEvalHub: A Large-Scale Chinese Benchmark for Evaluating Medical Large Language Models,
  year = {2024},
  publisher = {AAAI},
  journal = {Proceedings of Thirty-Eighth AAAI Conference on Artificial Intelligence(AAAI-2024)},
}
