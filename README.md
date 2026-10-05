# csv-json.py
import csv
import json


def read_csv(filename):
    with open(filename, "r") as f:
        data = list(csv.DictReader(f))
    return data


def write_json(data, filename):
    with open(filename, "w") as f:
        json.dump(data, f, indent=4)


def convert_csv_to_json(input_file, output_file):
    data = read_csv(input_file)
    write_json(data, output_file)
    return len(data)


if __name__ == "__main__":
    input_file = "students.csv"
    output_file = "students.json"

    count = convert_csv_to_json(input_file, output_file)

    print(f"{count} rows converted successfully.")

    with open(output_file, "r") as f:
        print(f.read())
