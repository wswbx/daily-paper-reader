---
title: Interpretable Predictive Modeling for Medical Data Using Boolean Rule-aware Regression
title_zh: 基于布尔规则感知的医学数据可解释预测建模
authors: "Eskandarian, M., Malekpour, S. A."
date: 2026-05-18
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.14.725084v1.full.pdf"
tags: ["query:sr"]
score: 6.0
evidence: 布尔规则回归在可解释性上类似于符号回归
tldr: 针对深度学习模型在临床应用中解释性不足的问题，提出基于布尔规则的回归框架RBBR，自动从数据中提取最多三个特征的逻辑与组合，通过岭回归预测疾病风险，并利用贝叶斯信息准则选择最优规则集。在肺癌、乳腺癌、心衰及糖尿病等六个真实数据集上，RBBR生成了简洁且临床意义明确的规则，如性别相关症状组合，解释力最高达R²=0.92，同时保持有竞争力的判别性能。该方法弥合了预测精度与临床可用性之间的鸿沟，使 clinicians能够验证预测、识别高危患者、分层亚群，并促进共享决策。
source: biorxiv
selection_source: fresh_fetch
motivation: 黑盒深度学习模型虽预测精准，但缺乏可解释性，阻碍临床信任与安全应用，亟需透明且符合临床推理的预测框架。
method: 提出RBBR，自动提取最多三个特征的逻辑与组合作为布尔规则，通过岭回归预测疾病结局，并用贝叶斯信息准则选择最简洁的规则集。
result: 在六个医疗数据集上，RBBR生成简洁临床规则，如糖尿病中性别-症状组合，解释力R²最高达0.92，且判别性能有竞争力。
conclusion: RBBR提供逻辑透明的决策规则，匹配临床推理，弥合预测精度与床旁可用性，增强诊断信心与安全整合。
---

## 摘要
目的在临床实践中，准确预测疾病风险必须伴随着透明、人类可理解的解释，以支持诊断信心、指导治疗决策，并满足伦理和监管标准。尽管深度神经网络在癌症检测和糖尿病风险分层等任务中实现了高预测性能，但其黑箱性质阻止临床医生理解预测背后的推理，严重限制了信任和安全性融入患者护理。

方法我们提出了基于回归的布尔规则（RBBR）框架，该框架直接从患者数据中自动推导出临床可解释的布尔规则。RBBR生成最多三个临床特征的人类可读合取（逻辑与组合），将其转换为岭回归的输入以预测二分类或多分类疾病结局，通过正则化系数估计规则重要性，并使用贝叶斯信息准则选择最简约且最具预测力的规则集。

结果将RBBR应用于六个真实医学数据集（肺癌筛查与分期、威斯康星和诊断性乳腺癌、心力衰竭和早期糖尿病风险），RBBR一致地生成了简洁、临床有意义的规则——例如，糖尿病中的性别特异性症状组合、乳腺癌中的不同组织病理学子群、以及肺癌中的症状-风险因素交互作用——具有强大的解释力（R²高达0.92）和有竞争力的区分能力。

结论通过提供与临床推理一致的逻辑、透明决策规则（如果症状A和B，则高风险），RBBR弥合了预测准确性与床旁可用性之间的差距，使临床医生能够验证预测、识别高风险患者、分层亚群，并在常规护理中增强共享决策。

## Abstract
PurposeIn clinical practice, accurate prediction of disease risk must be accompanied by transparent, human-understandable explanations to support diagnostic confidence, guide therapeutic decisions, and meet ethical and regulatory standards. While deep neural networks achieve high predictive performance in tasks such as cancer detection and diabetes risk stratification, their black-box nature prevents clinicians from understanding the reasoning behind predictions, severely limiting trust and safe integration into patient care.

MethodsWe present Regression-Based Boolean Rule (RBBR), a framework that automatically derives clinically interpretable Boolean rules directly from patient data. RBBR generates human-readable conjunctions (logical AND combinations) of up to three clinical features, transforms them into inputs for ridge regression to predict binary or multi-class disease outcomes, estimates rule importance via regularized coefficients, and selects the most parsimonious and predictive rule sets using the Bayesian Information Criterion.

ResultsApplied to six real-world medical datasets (lung cancer screening and staging, Wisconsin and diagnostic breast cancer, heart failure, and early-stage diabetes risk), RBBR consistently produced concise, clinically meaningful rules - e.g., gender-specific symptom combinations in diabetes, distinct histopathological subpopulations in breast cancer, and symptom-risk factor interactions in lung cancer - with strong explanatory power (R2 up to 0.92) and competitive discrimination.

ConclusionBy delivering logical, transparent decision rules aligned with clinical reasoning (if symptom A and B, then high risk), RBBR bridges the gap between predictive accuracy and bedside usability, enabling clinicians to validate predictions, identify high-risk patients, stratify subpopulations, and enhance shared decision-making in routine care.