## WikiWiki - a large scale entity typing dataset

WikiWiki dataset curates (mentions, entity_id, entity_type_id) triples from `10M` wikipedia documents. WikiWiki contains `~2.2M` entities comprising of `40K` entity types referencing `~39M` mentions across documents.

Each instance in the dataset contains a `context` that represents a paragraph from the document,  `mention2entity` mapping mentions (ie., surface forms of entities) to `qid` from Wikidata and also a `entity2type` field that maps each `entity qid` to a `type qid` in Wikidata. We also release a `glossary` that contains names and natural language descriptions of each `entity qid` and `type qid`. Here is a example instance from the dataset.

```
{
	"context": "After exiting the Fort Pitt Tunnel, US 19 Truck/I-376/US 22/US 30 cross the Monongahela River on the Fort Pitt Bridge, arriving on the Golden Triangle of downtown Pittsburgh. The route meets the southern terminus of Interstate 279 here, and I-376/US 22/US 30 head eastward, while US 19 Truck separates from them and joins I-279 on its northward trek. The two routes then cross the Allegheny River on the Fort Duquesne Bridge. North of the bridge, I-279 and US 19 Truck interchange with the southern terminus of Pennsylvania Route 65 at exit 1C of I-279. Exit 1B is to PNC Park and exit 1C is for Heinz Field. At exit 1D and 2A, I-279 southbound splits into HOV lanes at the Interstate 279 Interchange. The Interstate 279 interchange involves the northern terminus of Interstate 579 and the southern terminus of Pennsylvania Route 28.",
	"mention2entity": {"Monongahela River": ["Q643780"], "Fort Pitt Bridge": ["Q5471837"], "downtown Pittsburgh": ["Q11331506"], "Golden Triangle": ["Q11331506"], "Interstate 279": ["Q933990"], "I-279": ["Q933990"], "Allegheny River": ["Q686021"], "Fort Duquesne Bridge": ["Q5471105"], "Pennsylvania Route 65": ["Q1053127"], "PNC Park": ["Q1151177"], "Heinz Field": ["Q1067148"], "HOV lanes": ["Q285496"], "Interstate 579": ["Q934218"], "Pennsylvania Route 28": ["Q1052549"]},
	"entity2type": {"Q1151177": ["Q483110"], "Q285496": ["Q1941931"], "Q5471105": ["Q818882"], "Q5471837": ["Q818882"], "Q934218": ["Q34442"], "Q933990": ["Q34442"], "Q686021": ["Q4022"], "Q1067148": ["Q483110"], "Q1053127": ["Q34442"], "Q1052549": ["Q34442"], "Q11331506": ["Q738570"], "Q643780": ["Q4022"]}}
}
```
Sample entry of a mentioned `qid` from the glossary file

```
Q11331506	Downtown Pittsburgh	central business district of Pittsburgh, Pennsylvania, United States of America	central business district||golden triangle
```

We create this dataset using hyperlink information in wikipedia articles and their mapping to `qid` in wikidata. As hyperlinks are incomplete we perform additional processing to detect more (mention, entity, entity-type) triples. Please refer to Section 3 in the paper for details.

## Paper

WikiWiki provides a large scale dataset for linking, entity typing. In the paper below we focus on using the dataset to:
- Instill type knowledge into language models and show how they can benefit downstream tasks.
- Formulate entity typing as a generative task, to explore using large pre-trained language models to infer types unknown to existing ontologies.
- We use WikiWiki as a benchmark for fine-grained entity typing. WikiWiki is significantly larger and less noisy than existing benchmarks.

```bibtex
[Li et al. 2022]
@inproceedings{li22instilling,
  title = "Instilling type knowledge in language models via multi-task QA",
  author = "Shuyang Li and Mukund Sridhar and Chandana Satya Prakash and Jin Cao and Wael Hamza and Julian McAuley",
  year = "2022",
  booktitle = "Findings of the 2022 North American Chapter of the Association for Computational Linguistics (NAACL)"
}
```

## Dataset statistics

The table below shows high level statistics of the dataset:

|                                 | Train |  Test | Test (Unseen Entities) |
|---------------------------------|------ |-------|------------------------|
| Documents                       | 10.0M |  5.0K |        5.0K            |
| Unique Entities                 |  2.2M | 14.1K |        6.0K            |
| Unique Types                    | 40.6K |  4.0K |        1.2K            |
| # of Mentions                   | 38.7M | 19.3K |        6.4K            |
| # Type references               | 43.8M | 21.5K |        6.5K            |

## Getting Started

We will release the data in the following files:
- `train.jsonl` : consists of all training instances used in our pretraining experiments
- `test_seen_entities.jsonl` : our testset containing entities seen in training
- `test_unseen_entities.jsonl` : our testset containing unseen entities & hence possibly unseen types, not seen in training.
- `glossary.tsv` : glossary file where each line is has 3 columns (qid, name, natural language description from wikidata)

`Accessing the data : Steps to access & download the above files will updated here shortly.` 

## Cite

If you use this dataset, please cite the following paper:

```
[Li et al. 2022]
@inproceedings{li22instilling,
  title = "Instilling type knowledge in language models via multi-task QA",
  author = "Shuyang Li and Mukund Sridhar and Chandana Satya Prakash and Jin Cao and Wael Hamza and Julian McAuley",
  year = "2022",
  booktitle = "Findings of the 2022 North American Chapter of the Association for Computational Linguistics (NAACL)"
}
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License Summary

The documentation is made available under the Creative Commons Attribution-ShareAlike 4.0 International License. See the LICENSE file.

The sample code within this documentation is made available under the MIT-0 license. See the LICENSE-SAMPLECODE file.
