# Agent-Medical-2505

This is a built-from-scratch, fully customized language-model LM agent, with specialty in answering medical questions.

This multi-agent-system defines a memory with fast random access (via hashmap), which is also saved to disk as a json file everytime the mem is updated. 

![Screenshot from 2025-06-03 16-34-06](https://github.com/user-attachments/assets/74e366bf-f928-4abf-b648-13ffcc8ce41d)


For example, see the following comprehensive medical case, where we are asking the potential disease that causes these problems for the patient.

```
A 55-year-old woman presented to the emergency department (ED) with the chief complaint of headache for three days, associated with nausea, vomiting, and visual changes. The headache was described as being sudden in onset, constant, bilateral, retro-orbital, and throbbing. The pain was a six out of ten in intensity. The pain was not alleviated with over the counter acetaminophen use. She was not able to describe any alleviating or exacerbating factors. The visual changes were described by the patient as “blurry vision” and “double vision” affecting her left eye greater than her right. She reported photophobia and difficulty keeping the left eye open. The patient described this difficulty of keeping the eye open as a weakness and not secondary to pain. She had approximately five episodes of non-bloody and non-bilious vomiting over the past three days and reported inability to tolerate her home medications. She also reported a sore throat and cough productive of yellow sputum for the previous two to three days, but denied fever, chills, chest pain, hemoptysis, or dyspnea.
Her past medical history included essential hypertension, hyperlipidemia, and a remote history of uterine fibroids associated with iron deficiency anemia. Prescribed medications included losartan 25 milligrams (mg) and hydrochlorothiazide 12.5 mg. She had no known drug allergies, did not smoke, drink alcohol, or use illicit drugs. She was unemployed and lived alone. The patient was post-menopausal and was pregnant three times-two of which were normal spontaneous deliveries with two living children and one prior abortion.
Vital signs were: temperature 98.8° Fahrenheit, heart rate 84 beats per minute, blood pressure 135/74 millimeters of mercury, respiratory rate of 18 breaths per minute and room air oxygen saturation 97%. Her body mass index was 42 (normal 18.5–24.9). Complete physical examination was unremarkable except her left eye’s lateral gaze was restricted by approximately 25%. Her visual acuity was 20/25 and 20/30, right and left eyes, respectively. Initial laboratory testing were resulted (Tables 1 and 2). An electrocardiogram was performed (Image 1).

Table 1Complete blood cell count.
Serum hematology test	Value (reference range)
Complete blood cell count
 White blood cells	14.9 × 103/uL (4.0–11.0)
 Hemoglobin	14 g/dL (12.0–16.0)
 Hematocrit	43% (36.0–48.0)
 Platelets	225 × 103/uL (150–450)
Differential
 Neutrophils	78% (35.0–80.0)
 Lymphocytes	13% (20.0–50.0)
 Monocytes	7% (2.0–12.0)
 Eosinophils	0.6% (0.0–7.0)
 Basophils	0.8% (0.0–2.0)
uL, microliters; g, grams; dL, deciliter.

Table 2Chemistry results.
Serum chemistry test	Value (reference range)
Complete metabolic panel
 Sodium	128 mmol/L (133–145)
 Potassium	3.4 mmol/L (3.5–4.8)
 Chloride	88 mmol/L (97–110)
 Bicarbonate	27 mmol/L (23–30)
 Blood urea nitrogen	7 mg/dL (6–20)
 Creatinine	0.7 mg/dL (0.5–1.0)
 Glucose	81 mg/dL (70–109)
 Albumin	4.0 g/dL (3.5–5.2)
 Bilirubin	1.0 mg/dL (<= 1.0)
 Alkaline phosphatase	87 U/L (35–105)
 Total protein	8.5 g/dL(6.0–8.3)
 Aspartate transaminase	18 U/L (0–40)
 Alanine aminotransferase	11 U/L (0–33)
Additional chemistries
 Troponin	<0.01 ng/mL (0.00–0.30)
mmol, millimoles; L, liter; mg, milligram; dL, deciliter; U, units; ng, nanogram; mL, milliliter.

Image 1
Normal sinus rhythm at 64 beats per minute with sinus arrhythmia.
```

and here is the summarized answer:

```
<ResponseToUser>
The patient's presentation suggests a combination of increased intracranial pressure (ICP) and electrolyte abnormalities. Key considerations include:

1. **Idiopathic Intracranial Hypertension (IIH)**: 
   - Strongly indicated by obesity (BMI 42), headache, nausea/vomiting, sixth nerve palsy (left eye lateral gaze restriction), and visual blurring. 
   - Hyponatremia (Na 128 mmol/L) may be secondary to SIADH or thiazide-induced volume depletion, but IIH itself can cause mild hyponatremia via cerebral edema.

2. **Syndrome of Inappropriate Antidiuretic Hormone (SIADH)**:
   - Triggered by respiratory infection (yellow sputum, elevated WBC) or hydrochlorothiazide use. 
   - Hypokalemia (K 3.4 mmol/L) and low chloride (Cl 88 mmol/L) support this, though thiazide-induced hypokalemia must also be considered.

3. **Infectious Causes**:
   - **Gradenigo Syndrome** (mastoiditis with sixth nerve palsy and facial pain) or sinusitis-related meningitis, given sore throat/yellow sputum and elevated WBC.
   - **Sphenoid sinus aspergillosis** could cause focal cranial nerve palsies and hyponatremia.

4. **Structural Lesions**:
   - Pituitary macroadenoma, aneurysm, or tumor compressing the abducens nerve must be excluded via **immediate neuroimaging (MRI/CT with contrast)** and **lumbar puncture** (to measure opening pressure and rule out infection/hemorrhage).

5. **Thiazide-Induced Electrolyte Imbalance**:
   - Hydrochlorothiazide contributes to hyponatremia and hypokalemia via volume depletion or SIADH.

**Recommended Actions**:
- **Urgent neuroimaging** (MRI brain with contrast/MRA) to exclude structural pathology.
- **Lumbar puncture** to assess opening pressure (elevated in IIH) and CSF analysis (cell count, protein, glucose).
- **Electrolyte correction**: Gradual sodium correction (<10-12 mmol/L/24h) to prevent osmotic demyelination. Potassium repletion if symptomatic.
- **Address infection**: Broad-spectrum antibiotics (e.g., amoxicillin-clavulanate) pending culture results if sinusitis is suspected.
- **Discontinue hydrochlorothiazide** temporarily until hyponatremia resolved.

**Differential Exclusion**:
- Cerebral salt-wasting syndrome (less likely without severe neurologic injury).
- Vasculopathic sixth nerve palsy (less likely given acute presentation and ICP signs).
- Malignancy (e.g., nasopharyngeal carcinoma) requires imaging/radiology correlation.

This patient requires immediate evaluation in the emergency setting to prevent vision loss or neurologic deterioration.
</ResponseToUser>
```

The response includes lists that point to the medical references per list items generated by the agent, For example see:

```
1. The patient's left sixth nerve palsy and visual changes (blurry/double vision) suggest increased intracranial pressure (ICP), commonly seen in idiopathic intracranial hypertension (IIH) in obese individuals (BMI 42). This condition is characterized by headache, nausea, vomiting, and visual deficits. <REFERENCE>DID=241203110002157,SID=joh</REFERENCE>, <REFERENCE>DID=240927412005366,SID=sch</REFERENCE>, <REFERENCE>DID=241104020117753,SID=pmd</REFERENCE>  
2. The hyponatremia (sodium 128 mmol/L) could result from syndrome of inappropriate antidiuretic hormone secretion (SIADH), which may be triggered by her respiratory infection (yellow sputum, elevated WBC) or hydrochlorothiazide use. SIADH is associated with hyponatremia and can exacerbate ICP-related symptoms. <REFERENCE>DID=240927413009447,SID=wal</REFERENCE>, <REFERENCE=DID=241104026237593,SID=pmd</REFERENCE>, <REFERENCE=DID=241104008573958,SID=pmd</REFERENCE>  
3. The elevated white blood cell count (14.9 × 10³/μL) and respiratory symptoms (sore throat, yellow sputum) suggest an infectious etiology, such as sinusitis or pneumonia, which could contribute to SIADH or localized infections (e.g., sphenoid sinus aspergillosis) causing sixth nerve palsy. <REFERENCE=DID=241104008949301,SID=pmd</REFERENCE>, <REFERENCE=DID=240927413009447,SID=wal</REFERENCE>, <REFERENCE=DID=241104001307468,SID=pmd</REFERENCE>  
4. Hydrochlorothiazide use is a potential cause of hyponatremia and hypokalemia (3.4 mmol/L) due to SIADH or volume depletion. This diuretic can also exacerbate electrolyte imbalances in the setting of vomiting-induced volume loss. <REFERENCE=DID=241203180000594,SID=pmd</REFERENCE>, <REFERENCE=DID=240927413009447,SID=wal</REFERENCE>, <REFERENCE=DID=240927119001137,SID=toy</REFERENCE>  
5. Structural causes of sixth nerve palsy, such as pituitary macroadenoma with apoplexy, cerebral aneurysms, or cholesterol granuloma, must be considered. These lesions can compress the abducens nerve and elevate ICP. <REFERENCE=DID=241104035985120,SID=pmd</REFERENCE>, <REFERENCE=DID=241104028261154,SID=pmd</REFERENCE>, <REFERENCE=DID=241104031790372,SID=pmd</REFERENCE>  
6. Cerebral salt-wasting syndrome (CSWS) is another possible cause of hyponatremia, linked to intracranial pathology (e.g., increased ICP from IIH or infection) and characterized by renal salt loss. This condition may explain the hypokalemia and low chloride (88 mmol/L). <REFERENCE=DID=241104010364700,SID=pmd</REFERENCE>, <REFERENCE=DID=241104011219225,SID=pmd</REFERENCE>, <REFERENCE=DID=240927412005366,SID=sch</REFERENCE>  
7. The patient’s history of hypertension and use of thiazides places her at risk for vasculopathic sixth nerve palsy, which can occur due to small vessel disease or microvascular ischemia. <REFERENCE=DID=241203131000157,SID=nel</REFERENCE>, <REFERENCE=DID=241104025449936,SID=pmd</REFERENCE>  
8. Neuroimaging (MRI/CT) and lumbar puncture are critical to evaluate for structural lesions (e.g., tumors, aneurysms) and measure opening pressure to confirm IIH or other ICP-related conditions. <REFERENCE=DID=240927412005366,SID=sch</REFERENCE>, <REFERENCE=DID=241104025449936,SID=pmd</REFERENCE>  
9. The absence of fever or focal deficits makes primary infections like meningitis less likely, though localized infections (e.g., sphenoid sinus aspergillosis) remain a consideration. <REFERENCE=DID=240927421001011,SID=cas</REFERENCE>, <REFERENCE=DID=241104001307468,SID=pmd</REFERENCE>  
10. Neoplastic processes, such as skull base tumors or metastatic disease, could cause sixth nerve palsy and hyponatremia through paraneoplastic mechanisms or mass effect. <REFERENCE=DID=241104008216020,SID=pmd</REFERENCE>, <REFERENCE=DID=241104017038044,SID=pmd</REFERENCE>  
```

<br>

<br>

The following is an example prompt to define the "Planner" agent. This example uses a local QwQ language model (qwq-32b-q8_0.gguf). QwQ is the reasoning model of the Qwen series. This example runs the inference on 'llama_cpp'. Llama.cpp is a software library written in C/C++ designed for efficient inference of large language models.

```
AgentPlannerMedical = """<|im_start|>user
You are a planning agent. If you do not know the answer, reply I don't know, don't make things up.
You need to follow these instructions strictly:
1.Generate a plan of actions, 'Action Plan', do not take any action.
2.What 'Action Plan' is: a numbered list of steps to take in order to answer the question marked up by the tags <Question> and </Question>.
3.Mark up each of the steps by respective tags <ActionPlanStep1> and </ActionPlanStep1>, then <ActionPlanStep2> and </ActionPlanStep2>, then <ActionPlanStep3> and </ActionPlanStep3> and so forth.
4.You need to use a Tool per step in your 'Action Plan'. Each tool can be used in more than one step, or in no step at all.
5.The Tools at your disposal are:
 5.1.'PythonCodeExecutor': it accepts a python code, executes it in python, returns the execution output back. 
  5.1.1.Install packages first as a separate step (before executing any other python code), using the method: import sys; import subprocess; subprocess.check_call([sys.executable, "-m", "pip", "install", package]). 
  5.1.2.Try to combine PythonCodeExecutor steps hence less such steps in the ActionPlan. 
  5.1.3.Use print statements to print the results.
 5.2.'ResponseComposer': it takes the Question, the ActionPlan, and the answers to the steps of the ActionPlan, then it composes the final response to the end-user who asked the Question.
 5.3.'HumanInTheLoop': when you are not sure what to do or what you are planning is correct, call the human supervisor by adding a step with the tool HumanInTheLoop.
 5.4.Tools for medical Questions: when you see that the Question is a medical or health question, use the following tools to get an answer for the Question:
  5.4.1.'ConvertUserQToIrKeywords': If Question is a natural language question, use the tool ConvertUserQToIrKeywords to generate equivalent keywords (call them the IR-query) that are optimal for information retrieval (IR) via keyword-search-engine.
  5.4.2.'MedicalKnowledgeBaseSearcher': Send the IR query (keywords and their synonyms) derived from Question, to MedicalKnowledgeBaseSearcher and it will return the best medical knowldegebase (KB) records that respond to the Question.
  5.4.3.'RAG': for medical Questions, after you got relevant KB records from the MedicalKnowledgeBaseSearcher, then call RAG to generate an answer given the Question and the KB records.
6.Within each step <ActionPlanStep1>, <ActionPlanStep2>, <ActionPlanStep3> and so forth, put the name of the Tool the step is using within the tags <Tool> and </Tool>.
 6.1.For steps where the tool is <Tool>PythonCodeExecutor</Tool>, generate the python code to execute such step, and include it in the tags <PyCode> and </PyCode>. When generating python code, Use alternative resources that do not require API keys.
 6.2.For steps of medical Question, you do not add any <PyCode> tag, nor generate any python code.
 6.3.Do not add anything else, no explanation etc, to the steps <ActionPlanStep1>, <ActionPlanStep2>, <ActionPlanStep3> and so forth.
7.Add a final step for composing response to the end-user who asked the Question.
8.Use the tags <IfMedicalQuestion> and </IfMedicalQuestion> and add the value 1 or 0 depending on the Question being a medical/health question or not.

<Question>
"""+LlmQstn22+"""
</Question>
|im_end|>
<|im_start|>assistant
"""
```

