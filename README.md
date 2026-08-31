# Housing-Data-in-Malaysia

A C-based data processing project developed for the **COMP6047001 – Algorithms and Programming** course (Bina Nusantara University, School of Computer Science). The program reads a CSV dataset containing 3,939 rows of housing data from Malaysia and performs statistical description, keyword-based search, and alphabetical sorting on the records.

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Examples](#examples)
- [Author](#author)
- [Notes](#notes)

## Overview

This project implements three separate C programs that operate on the same housing dataset:

1. **Describe**: summarizes column-level statistics (frequency, min, max, average).
2. **Search Data**: searches records using a `DataX in ColumnName` query format, supporting substring matching.
3. **Alphabetize**: sorts a list of location names alphabetically, based on Deitel's *C How to Program*, Chapter 8, Exercise 8.21.

Each solution reads the header row of the CSV file, skips it, and loads the remaining rows into record variables (arrays/structs) before performing its respective operation.

## Dataset

The dataset (`file.csv`) contains 3,939 rows of housing listings in Malaysia with no missing values, and includes the following columns:

| Column | Description |
|---|---|
| `Location 1` (`loc1`) | Primary location/neighborhood |
| `Location 2` (`loc2`) | Secondary location (e.g., city) |
| `Price` | Listing price |
| `Rooms` | Number of rooms |
| `Bathrooms` | Number of bathrooms |
| `CarParks` | Number of car park spaces |
| `Type` | Property type (e.g., Built-up, Land-area) |
| `Area` | Property area |
| `Furnish` | Furnishing status (Fully/Partly/Unfurnished) |

## Project Structure

```
Housing-Data-in-Malaysia/
├── src/
│   ├── solution-1.cpp   # Describe function
│   ├── solution-2.cpp   # Search Data function
│   └── solution-3.cpp   # Alphabetize function
├── data/
│   └── file.csv         # Housing dataset
├── docs/
│   └── 2602089143-JonathanAlvindoFernandi_AoL-CaseStudy.pdf  # Explanation and flowcharts for each solution
├── .gitignore
└── README.md
```

## Features

### 1. Describe

Prompts the user for a column name, then displays:

- For `loc1`, `loc2`, `Rooms`, `Bathrooms`, `CarParks`, `Type`, or `Furnish`: the frequency of each unique value, along with the maximum and minimum frequency.
- For `Area` and `Price`: only the minimum, maximum, and average values (since these are continuous, not discrete, values).

### 2. Search Data

Accepts a query in the format `DataX in ColumnName` (parsed without using three separate string inputs) and displays all matching records. Supports:

- Exact or partial (substring) matching, e.g., `Partly in furnish` or `pong in loc1`.
- A clear message when no matching data is found.
- Search restricted to columns other than `Area` and `Price`.

### 3. Alphabetize

Implements an alphabetization algorithm (adapted from Deitel, *C How to Program*, Chapter 8, Exercise 8.21) applied to the `Location 1` column, sorting the list of location names alphabetically.

## Getting Started

### Prerequisites

- A C compiler such as `g++` (via [MinGW](https://www.mingw-w64.org/) on Windows, or pre-installed on Linux/macOS)
- Git

### Clone the Repository

```bash
git clone https://github.com/jonathanafernandi/Housing-Data-in-Malaysia.git
cd Housing-Data-in-Malaysia
```

### Compile

Compile each solution individually:

```bash
g++ src/solution-1.c -o solution-1
g++ src/solution-2.c -o solution-2
g++ src/solution-3.c -o solution-3
```

Make sure `file.csv` is placed in the same directory as the compiled executable, or update the file path inside the source code accordingly.

## Usage

Run each compiled program from the terminal:

```bash
./solution-1   # Describe
./solution-2   # Search Data
./solution-3   # Alphabetize
```

## Examples

**Describe - example for `loc1`:**

```
Enter column name: loc1
Mont-Kiara        45
Cheras            62
...
Maximum value Cheras with frequency 62
Minimum value ... with frequency ...
```

**Search Data - example query:**

```
Enter DataX in ColumnName: Partly in furnish
```

```
Enter DataX in ColumnName: pong in loc1
```

If no match is found, the program prints a message indicating that the searched data does not exist in the record.

**Alphabetize - example:**

Sorts a list of `Location 1` values into alphabetical order and prints the sorted list.

## Author

**Jonathan Alvindo Fernandi**  
Computer Science, School of Computer Science, Bina Nusantara University  
Course: COMP6047001 – Algorithms and Programming (Class LC01)

## Notes

- All solutions are implemented in C, using only standard libraries (`stdio.h`, `string.h`).
- Each solution is accompanied by a flowchart (included in `docs/`) explaining the logic of the program and its sub-functions.
