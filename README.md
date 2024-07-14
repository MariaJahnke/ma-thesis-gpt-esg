# Using ChatGPT for assistance in analysing compliance with CSRD in ESG reports

This repository includes all data for the master thesis to conduct a compliance analysis of the CSRD regulations with DAX40 company reports. The reports of the DAX40 companies are stored in a PDF format in the folder [esg_reportings](esg_reportings) as well as the used [CSRD regulation](G1-3-regulation.pdf).

## Zero-shot prompting
For the zero-shot prompting approach, the input Excel [zeroshot.xlsx](analysis/zeroshot.xlsx) includes the company name, the file path to the corresponding company report, the assistant_ID and the prompt.
The [zeroshot Jupyter notebook](zeroshot.ipynb) contains the scripts to run the prompts using the OpenAI assistant API. For testing a personal API-key must be added. The prompt responses are then saved into the same [zeroshot.xlsx](analysis/zeroshot.xlsx) in the respective company row. 

For manual evaluation the [zeroshot results](analysis/zeroshot.xlsx) were copied to [zeroshot_evaluated.xlsx](analysis/zeroshot_evaluated.xlsx). It is a separated file used as data input for further visualizations via [graph.ipynb](graph.ipynb).

## Advanced prompting
For the advanced prompting approach, the input Excel [fewshot](analysis/fewshot.xlsx) includes the company name, the file path to the corresponding company report, assistant_ID and the three prompts.

Consistently with the zero-shot prompting approach, the [fewshot jupyter notebook](fewshot.ipynb) runs the prompts. Answers are also copied to [fewshot_evaluated.xlsx](analysis/fewshot_evaluated.xlsx) and used for further visualization via [graph.ipynb](graph.ipynb).

## Fine-tuning
The [fine-tuning jupyter notebook](finetuning.ipynb) includes scripts for:
1. converting [ESG report PDFs](./esg_reportings) to [text files](./finetuning-input)
2. validating the length of the text in tokens according to OpenAI limits and requirements
3. manual step: shortening the text if needed (step 2)
4. generating the [training.jsonl](./finetuning/training.jsonl) and [validation.jsonl](./finetuning/validation.jsonl) files, which will serve as input data for fine-tuning
5. manual step: uploading the jsonl files via the OpenAI interface for fine-tuning
6. running the [test dataset](./analysis/finetuning.xlsx) using the finetuned model -> prompt answers are saved into the same file

For evaluation, the results are copied into the [finetuning_evaluated.xlsx](analysis/finetuning_evaluated.xlsx) and used for visualization via [graphs.ipynb](graph.ipynb).