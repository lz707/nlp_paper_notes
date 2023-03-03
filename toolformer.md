#[Toolformer: Language Models Can Teach Themselves to Use Tools]( https://arxiv.org/abs/2302.04761)

Written in 2023

tl;dr: The authors first employ in-context learning to enable GPT to modify prompts to resemble API calls, while ensuring that the API calls yield "helpful" responses (i.e., they minimize the loss compared to the original next tokens). Then they leverage this data to fine-tune GPT and evaluate its performance on standard NLP tasks, with a focus on whether the model can effectively make API calls to enhance accuracy. Their findings suggest that, in many cases, the fine-tuned model does make API calls to help it answer questions and that API indeed lead to improved performance.

#### Overall impression
The authors used a creative method to build the fine-tune dataset without human annotation, which is quite impressive. Their use of in-context learning to enable GPT to generate annotated data autonomously represents a promising avenue for expanding the capabilities of the LLMs. 

#### Key ideas
- The authors devised a method for constructing a fine-tuning dataset without requiring human annotation. They began by presenting a prompt example and leveraged GPT's in-context learning capabilities to generate API calls autonomously. They then executed the API calls and filtered out those that did not improve the loss compared to the next tokens. Specifically, they retained only the API calls that contributed to achieving a more accurate result. The resulting dataset was then used for fine-tuning.
![](https://i0.wp.com/kikaben.com/wp-content/uploads/2023/02/image-9.png?resize=415%2C540&ssl=1)

![](https://i0.wp.com/kikaben.com/wp-content/uploads/2023/02/image-10.png?resize=960%2C199&ssl=1)

-Experiment results: 
Toolformer outperformed in the following tasks:
-Question Answering (by making QA API calls)
-Calculation(by utilizing a calculator)
-Calendar. Interestingly, when performing on tempLAMA dataset, which is built from Wikidata that contains cloze queries about facts with time/dates, the model appropriately opted to call the QA API, which makes sense given the nature of the task. On the other hand, for the DATESET task, the model did utilize calendar API and outperformed.

Toolformer underperformed in the Multilingual Question Answering task. The task provides a context paragraph in English, while the question is given in another language and the answer is asked to be provided in English. Apparently GPT-3 and OPT also failed miserably here, mostly because they still provided an answer in English. One notable weakness of current LLMs is their tendency to struggle with language mixing, which may be attributed to a scarcity of relevant training data. Using Chain-of-Thought type prompt could improve the results in current settings, as the task can be split into two steps. Adding more translation data in future LLM trainings would improve on this in a fundamental way.
 
-Fine-tune data size: The authors mentioned up to 25K data was used for fine-tuning, but they did not provide a breakdown by tasks. Below is the number of examples with different filtering rate. Noticeably, Calculator and Calendar have much fewer data but the result was good. 
 


