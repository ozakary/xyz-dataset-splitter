# XYZ Dataset Splitter

A Python tool for splitting XYZ molecular dynamics trajectory files into training, validation, and test sets for machine learning applications.

## Features

- Split XYZ files by exact number of configurations
- Sequential or random splitting options
- Customizable output file naming
- Data preprocessing for MACE compatibility

## Requirements

- Python 3.6+
- No external dependencies (uses only standard library)

## Usage

### Basic Usage

```bash
python xyz_splitter.py input_file.xyz --train_size 800 --valid_size 100 --test_size 100
```

### Random Splitting

```bash
python xyz_splitter.py input_file.xyz --train_size 800 --valid_size 100 --test_size 100 --rand_split true
```

## Command Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `input_file` | Path to input XYZ file | Required |
| `--train_size` | Number of training configurations | Required |
| `--valid_size` | Number of validation configurations | Required |
| `--test_size` | Number of test configurations | Required |
| `--rand_split` | Use random splitting (`true`/`false`) | `false` |
| `--seed` | Random seed for reproducibility | `42` |
| `--output_prefix` | Prefix for output files | `water_xe_dataset` |

## Output Files

The script generates three files:
- `{prefix}_train.xyz` - Training set
- `{prefix}_valid.xyz` - Validation set  
- `{prefix}_test.xyz` - Test set

## Examples

```bash
# Sequential split with default names
python xyz_splitter.py data.xyz --train_size 1500 --valid_size 200 --test_size 300

# Random split with custom prefix
python xyz_splitter.py data.xyz --train_size 800 --valid_size 100 --test_size 100 --rand_split true --output_prefix my_dataset

# Custom seed for reproducibility
python xyz_splitter.py data.xyz --train_size 800 --valid_size 100 --test_size 100 --rand_split true --seed 123
```

## Notes

- The script validates that requested configurations don't exceed available data
- Sequential splitting takes configurations in order, random splitting shuffles first
- Headers are automatically processed for MACE compatibility
