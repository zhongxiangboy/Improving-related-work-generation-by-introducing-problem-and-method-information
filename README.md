# Improving-related-work-generation-by-introducing-problem-and-method-information
This work is an optimized approach with adopting problem and method information to generate related work section for scientific papers.

The baseline data used in this project is provided by: https://github.com/AhmedAbuRaed/SPSeq2Seq.  Our purpose is to verify the effect of problem-method information in related work section generation.

In order to automatically obtain the problem method information, we apply a title generation strategy to generate a title with the pattern "A based on B" for each article that needs to extract the problem method information (We assume that B is the Method of the problem A).  Although this strategy is risky, it has the convenience of not requiring  data annotation, which is often the most time-consuming task in the training process of deep neural networks.

Meanwhile, in order to verify the effectiveness of our strategy, we also adopt another method to obtain the problem method information. DYGIE (https://github.com/dwadden/dygiepp) is a tool  that could automatically identify entities such as task and method from the input text.

Note: When DYGIE identifies multiple task entities or method entities, we choose the one with the largest phrase length to provide more information. For the case where the question word or method word cannot be identified, we use null values for its representation

Data uesd:
    1. The base training datasets in _filtered_ and _unfiltered_ are provided by https://github.com/AhmedAbuRaed/SPSeq2Seq
    
    2. The dataset in _filtered_mq_dygie_ and _unfiltered_mq_dygie_ are based on the base training data with the problem method information, which obtained 	through the open-source tool DyGIE.
    
    3. The dataset in _filtered_mq_title_ and _unfiltered_mq_title_ are based on the base training data with the problem method information, which obtained 	through the title generation strategy.
	

Model and Codes:

    1. For the title generation, we use point network: https://github.com/abisee/pointer-generator, because we hope the problem/method words in the original     text to be copied via pointing during sequence generation.

    2. PreSum model code can be found:https://github.com/nlpyang/PreSumm

    3. Transformer and BART model can be found in : https://huggingface.co/
