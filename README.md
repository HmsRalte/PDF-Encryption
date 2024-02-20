 # PDF-Encryption
Short Python Code for encrypting PDFs

In this code, we are using the following libraries:
1) PyPDF2

The rest if the code is very self explanatory as it is a very short code.
Definitions and explanations of the keywords will be written in the code as best I can.

---
 ### Parameters:
  -> input_pdf (str): Path to the input PDF file to be encrypted.
  
  -> output_pdf (str): Path to the output PDF file where the encrypted PDF will be saved.
  
  -> password (str): The password used for encrypting the PDF.

1. **with open(input_pdf, 'rb') as file:**

  *with statement is used to open the file in context manager, ensuring file is properly closed after its suite finishes or if an exception occurs*
  
  - open(input_pdf, 'rb'): Opens the file specified by input_pdf in binary read mode
  
  - 'rb': 'r' stands for read mode, and 'b' stands for binary mode, indicating file should be treated as a binary file
    
   *A binary file contains data in format composed of 0's and 1's unlike ASCII or UTF-8, PDFs are made to be read as binary file because they contain stricterd format that includes binary data*
    
   *When opening a PDF in binary mode ('rb') we're indicating to the prpogramming language that we want to read the file byte by byte without any character encoding.*
    
   *This is crucial for correctly interpreting the binary data within the PDF, which includes both textual content and binary-encoded elements like images.*
    
   - 'as file': assigns the file object to the variable file for further operations within the indented block.
    
   *Inside this block, we can perform operations such as reading, writing or processing the contents of the opened PDF file. Once this block is exited  the file is automatically closed thanks to the 'with' statement.*

2. **pdf_reader = PyPDF2.PdfReader(file)**
   
   - file: The file object representing the opened PDF file in binary mode.

   - pdf_reader: This parameter provides methods to access and manipulate the contents of the PDF file.

3. **pdf_writer = PyPDF2.PdfWriter()**
   *the line initializes a PdfFileWriter object from the PyPDF2 library, which is used for creating or modifying PDF files.

   - pdf_writer: this object allows to add pages, annotations and other elements to create a new PDF file or modify an exisitng one (eg: pdf_writer.addPage(page))

4. **for page_num in range(len(pdf_reader.pages)):
            pdf_writer.add_page(pdf_reader.pages[page_num])**

   *we iterate through each page of the pdf_reader and adding each page to the pdf_writer*
   - pdf_reader: contains the opened PDF file.
   - page_num: represents the current page number in the iteration
   - pdf_reader.pages: its a list of all the pages in the PDF file and pdf_reader.pages represent the specific page at the current iteration.
   - The loop starts from page 0 (first page) and goes up to 'len(pdf_read.pages)- 1'.

   *adding the current page to the PdfFileWriter object*
   - pdf_writer: PdfFileWriter object used for creating or modifying a PDF file.
   *this line adds the current page ti the PdfFileWriter object which is being used in a new PDF file or modify an existing one.*
   - pdf_reader.pages[page_num]: represents the specific page being added to the PdfWriter
   *the loop continues until all pages form the PdfReader have been added to the PdfWriter*

5. **pdf_writer.encrypt(password)**
   
   *encrypts the PDF content using the specified password*
   
   - password(str): provided as an argument to the encypt method.
   
7. **with open(output_pdf, 'wb') as output_file:
            pdf_writer.write(output_file)**
   
   *opens a new PDF file in bimary write mode for saving the encypted content*
   - output_pdf(str): Path to  the output PDF file where the encrypted PDF will be stored
     *this opens a new PDF file in binary write mode using 'with' statement, "output_pdf" is the path to the file where the encypted pdf is stored( default root folder where the .py file is being run*
   - wb: w stands for write mode, b stands for binary mode.
   - output_file: file representing the opened output pdf ifle in binary write mode
     *this line writes the encrypted content stored in the pdf_writer to the output*
     *after this, the encypted content is saed to the specified output PDF file.*
