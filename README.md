# PDF-Encryption
Short Python Code for encrypting PDFs

In this code, we are using the following libraries:
1) PyPDF2

The rest if the code is very self explanatory as it is a very short code.
Definitions and explanations of the keywords will be written in the code as best I can.


 Parameters:
  -> input_pdf (str): Path to the input PDF file to be encrypted.
  -> output_pdf (str): Path to the output PDF file where the encrypted PDF will be saved.
  -> password (str): The password used for encrypting the PDF.

with open(input_pdf, 'rb') as file:

  #with statement is used to open the file in context manager, ensuring file is properly closed after its suite finishes or if an exception occurs
  
  #open(input_pdf, 'rb'): Opens the file specified by input_pdf in binary read mode
  
    -> 'rb': 'r' stands for read mode, and 'b' stands for binary mode, indicating file should be treated as a binary file
    
    # A binary file contains data in format composed of 0's and 1's unlike ASCII or UTF-8, PDFs are made to be read as binary file because they contain stricterd format that includes binary data
    
    # When opening a PDF in binary mode ('rb') we're indicating to the prpogramming language that we want to read the file byte by byte without any character encoding.
    
    # This is crucial for correctly interpreting the binary data within the PDF, which includes both textual content and binary-encoded elements like images.
    
    -> 'as file': assigns the file object to the vraible file for further operations within the indented block.
    
    -> Inside this block, we can perform operations such as reading, writing or processing the contents of the opened PDF file. Once this block is exited  the file is automatically closed thanks to the 'with' statement.
    
