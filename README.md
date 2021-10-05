This code provides models to extract intelligent information (company, address, date, total amount) from invoice documents based on natural language processing. The flamework mainly includes two steps. Firstly, text data extraction and processing by using text detector algorithm. And then recognizing the context by using recurrent neural network. 


## Pre-trained models
You can download the pre-trained models from [Google Drive](https://drive.google.com/drive/folders/1_5hhevbrEkQ0-1Duwbfs-TfTW2Mwwvic?usp=sharing)

## Installation

#### Ubuntu 18.04

To install InvoiceNet on Ubuntu 18.04, run the following commands:

```bash
git clone https://github.com/RijunLiao/invoice.git
cd InvoiceNet/

# Run installation script
./install.sh
```

The install.sh script will install all the dependencies, create a virtual environment, and install InvoiceNet in the virtual environment.

To be able to use InvoiceNet, you need to source the virtual environment that the package was installed in.

```bash
# Source virtual environment
source env/bin/activate
```

## Prediction

---

### Single invoice
To extract a field from a single invoice file, run the following command:

```bash
python predict.py --field enter-field-here --invoice path-to-invoice-file

# For example, to extract field total_amount from an invoice file invoices/1.pdf
python predict.py --field total --invoice invoices/1.pdf # just predict the amount
python predict.py --field comany address total date --invoice invoices/1.pdf # predict the omany address total date at the same time
```

---

### Multiple invoices
For extracting information using the trained InvoiceNet model, you just need to place the PDF invoice documents in one directory in the following format:

```
predict_data/
    invoice1.pdf
    invoice2.pdf
    ...
```

Run InvoiceNet using the following command:
```bash
python predict.py --field enter-field-here --data_dir predict_data/

# For example, for field 'total_amount'
python predict.py --field total --data_dir predict_data/  # just predict the amount
python predict.py --field comany address total date --data_dir predict_data/ # predict the omany address total date at the same time
```
---

## Reference
This implementation is largely based on the work of [InvoiceNet](https://github.com/naiveHobo/InvoiceNet)
