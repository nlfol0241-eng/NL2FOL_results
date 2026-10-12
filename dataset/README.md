# NL-to-Multi-Sorted-FOL Dataset

This directory contains the dataset used for translating natural-language database queries into Multi-Sorted First-Order Logic (FOL). Each example includes the original natural-language query, its corresponding SQL query, vocabulary and arity definitions, sort information, logical axioms, and the reference FOL representation.

## Dataset Structure

The dataset is stored as a JSON array. Each object follows this structure:

## Field Description

- **`id`**: Unique identifier of the dataset instance.
- **`NL`**: Natural-language representation of the query.
- **`SQL`**: Processed SQL query corresponding to the natural-language input.
- **`Vocabulary`**: Predicates, functions, and constants available for constructing the logical formula.
- **`Arity`**: Arity definitions for the vocabulary elements.
- **`Global Sorts`**: Sorts available globally for the instance.
- **`Sort Axioms`**: Constraints defining the valid sorts of predicate and function arguments.
- **`Axioms`**: Additional logical axioms associated with the instance.
- **`Gold FOL`**: Reference Multi-Sorted FOL formula and its free variables.


## Intended Use

## The dataset can be used for:

Training and evaluating natural-language-to-FOL systems
Evaluating constrained logical-form generation
Studying SQL-to-FOL and relational-query translation
Assessing vocabulary, arity, sort, and free-variable correctness
Comparing rule-based and large language model approaches to logical-form generation
Data Integrity

The order and values of dataset instances are preserved. Instance IDs are not renumbered or sorted during preprocessing. Only the required fields are retained and arranged in a consistent order.

## Loading the Dataset
Python
import json
 
with open("dataset/<dataset_file>.json", "r", encoding="utf-8") as file:
data = json.load(file)
 
print(f"Number of instances: {len(data)}")
print(data[0])

Replace <dataset_file>.json with the actual dataset filename.

## Citation

If you use this dataset in academic work, please cite the associated paper or repository. Citation information will be added upon publication.

## License

This dataset is distributed under the license specified in the root of this repository. Any source datasets or external resources remain subject to their respective licenses.
