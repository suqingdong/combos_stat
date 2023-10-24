# CombosStat: A utility tool designed to compute shared data statistics for given combinations of data samples

## Installation
```bash
python3 -m pip install combos_stat
```

## Usage
```bash
combos_stat -h
```

### *`1. stat`*
```bash
Usage: python -m combos_stat.bin.main stat [OPTIONS]

  Calculate statistics for shared data counts based on combinations of samples.

Options:
  -i, --input-file PATH           Path to the input data file  [required]
  -o, --output-file PATH          Path where the results will be saved  [default: output_stat.txt]
  -n, --num-samples INTEGER       Number of samples to compute  [required]
  -t, --share_type [intersection|union]
                                  Type of share to compute
  --header INTEGER                Row number to use as the column names  [default: 0]
  --sep TEXT                      Delimiter to use for reading the input file (e.g., "\t" for tab)
  --start-col INTEGER             Column index to start reading sample data from  [default: 1]
  --show-progress BOOLEAN         Show progress
  --chunksize INTEGER             The chunksize lines to read
  --chunk INTEGER                 The index of chunk
  -h, -?, --help                  Show this message and exit.


examples:
    combos_stat stat -h
    combos_stat stat -i input.txt -o output.txt -n 13 -t intersection
    combos_stat stat -i input.txt -o output.txt -n 13 -t intersection --chunksize 100 --chunk 2 [read 101-200 lines]
```

### *`2. plot`*
```
Usage: python -m combos_stat.bin.main plot [OPTIONS] RESULT_DIR

  Plot statistics

Options:
  -R, --Rscript TEXT  Path to the executable Rscript  [default: Rscript]
  -w, --write TEXT    Write the R code to a file
  -?, -h, --help      Show this message and exit.
  

examples:
    combos_stat plot -h
    combos_stat plot out/result
```

### *`3. batch`*
```bash
Usage: python -m combos_stat.bin.main batch [OPTIONS]

  Generate batch shells and SJM job

Options:
  -i, --input-file PATH    Path to the input data file
  -sep, --sep TEXT         Delimiter to use for reading the input file (e.g., "\t" for tab)
  -s, --start-col INTEGER  Column index to start reading sample data from  [default: 1]
  -t, --threshold INTEGER  The threshold to divide the combinations  [default: 200000]
  -O, --output-dir PATH    Path to the output directory  [default: .]
  --job TEXT               Generate SJM Job
  --no-check               Do not check queues for SJM
  -h, -?, --help           Show this message and exit.


examples:
    combos_stat batch -h
    combos_stat batch -i input.txt -t 200000 -O out
    combos_stat batch -i input.txt -t 200000 --job run.job
```

