# OCR-based Medical Data Extraction Project

This project was developed following the Codebasics Python course. If you're interested, you can find the course [here](https://codebasics.io/).

## Problem Statement

Health insurance companies need to adhere to government regulations when processing claims. This involves handling images of patient details and prescriptions sent by hospitals or individual doctors to extract relevant information. Currently, many insurance companies outsource this task to firms like "Mr. X Data Analytics," where employees manually transcribe the information from scanned images.

Mr. X Data Analytics uses software that displays scanned images on one side and requires manual data entry on the other. This process is prone to errors and becomes unmanageable during high-volume periods, such as pandemics. Additionally, insurance companies demand that the extracted data be provided within 24 hours, prompting Mr. X Data Analytics to seek an automated solution.

## Solution Approach

To address these challenges, we developed a program to automatically extract data from images. While automation cannot entirely replace human oversight, this solution significantly reduces the manual effort required. A human will still review the extracted data to ensure accuracy before submission.

We use Python, the pytesseract library for OCR, and regular expressions for data processing to achieve this.

## Technologies Used

- Python
- Object-Oriented Programming (OOP)
- pdf2image module
- OpenCV
- pytesseract
- Regular Expressions
- pytest
- Postman
- FastAPI

## Workflow
![workflow (1)](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/assets/158494053/38738977-07c8-4cc3-aaae-b2737562340b)

### PDF to Image Conversion

We use the pdf2image library to convert PDF documents to images for processing.

### Data Extraction Without Preprocessing
![dark_image (1)](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/assets/158494053/ad2a092d-a731-4dbe-b0e0-e5f80e492fe7)


Initial attempts to extract data from raw images were unsuccessful due to formatting issues, resulting in inaccurate data extraction.

#### Extracted Data (Without Preprocessing)
```
Dr John Smith, M.D
2 Non-Important Street,
New York, Phone (000)-111-2222

Name: Maria Sharapova Date: 5/11/2022

Address: 9 tennis court, new Russia, DC

Prednisone 20 mg
Lialda 2.4 gram

3 days,
or 1 month
```

### Image Processing

To improve accuracy, we preprocess the images using the OpenCV library. We first applied normal thresholding, which failed in areas with shadows or noise, leading to data loss.

#### Normal Thresholding Example
![filter_dark (1)](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/assets/158494053/0e0e7db0-7d38-47ae-bd36-f20d2e117e62)

We then adopted adaptive thresholding, which divides the image into sub-images and applies different threshold values to each, yielding much better results.

#### Adaptive Thresholding Example
![adaptive_filter_dark (1)](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/assets/158494053/8edb7c4e-3755-412a-9387-44f2e4cf9e83)

### Data Extraction After Preprocessing
```
Dr John Smith, M.D
2 Non-Important Street,
New York, Phone (000)-111-2222

Name: Marta Sharapova Date: 5/11/2022

Address: 9 tennis court, new Russia, DC

Prednisone 20 mg
Lialda 2.4 gram

Directions:

Prednisone, Taper 5 mg every 3 days,
Finish in 2.5 weeks
Lialda - take 2 pill everyday for 1 month
```

## Development Process

<hr>

### Notebook  
For all these above trials, used Jupyter Notebooks and developed small bits of functionality, which can be used later while designing the class.

[Notebooks](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/tree/main/notebooks)

<hr>

### OOPs Design

The code follows Object-Oriented Programming principles for extracting data from medical documents.

[Notebooks](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/tree/main/src)
<hr>

### Regular Expressions

We used regular expressions to match and extract patterns from the medical documents. Patterns were tested and refined using,

[regex101](https://regex101.com/)
<hr>

### Test-Driven Development

We employed test-driven development using the pytest module, writing test cases for each method and verifying functionality during development.

[Test cases](https://github.com/Harshith-VC/Medical_Data_Extraction-Python/tree/main/tests)

<hr>

### FastAPI

The project server is hosted using FastAPI, which offers several advantages:
- Built-in data validation
- Automatically generated documentation
- High performance
<hr>

### Postman

Since this is a backend project, we used Postman to test the server's HTTP responses.

<img width="700" alt="postman (2)" src="https://github.com/Harshith-VC/Medical_Data_Extraction-Python/assets/158494053/bca7ebf7-8c5d-4cf0-90c4-506692eedd0b">

### Result
This backend functionality can be integrated into the Mr.X Analytics existing software and data can be extracted automatically. The extracted data may have some errors, the person who is performing the work has to correct it and submit the response

### Benefits
- Mr.X Analytics can save at least of 30 secs for each document. It is small amount of time when looking for one document, but cumulatively it can save a tremendous amount of time which can help the company to complete more documents within the given time and make more profit
- The company doesn't have to hire extra people in the season time.
As it is a combination of automation and manual the error will be very much low.
