#pdf
This is how an HTTP response/request looks with content type set as pdf:
```js
HTTP/1.1 200 OK
Content-Type: application/pdf
Content-Disposition: attachment; filename="example.pdf"
Content-Length: 123456
Date: Sun, 17 Jul 2023 12:34:56 GMT

%PDF-1.7
%����
<< /Type /Catalog
   /Pages 2 0 R >>
endobj
2 0 obj
<< /Type /Pages
   /Kids [3 0 R]
   /Count 1 >>
endobj
3 0 obj
<< /Type /Page
   /Parent 2 0 R
   /Resources <<
      /Font <<
         /F1 4 0 R
      >>
   >>
   /Contents 5 0 R >>
endobj
4 0 obj
<< /Type /Font
   /Subtype /Type1
   /BaseFont /Times-Roman
   /Encoding /WinAnsiEncoding
>> 
endobj
5 0 obj
<< /Length 44 >>
stream
BT
/F1 24 Tf
100 700 Td
(Hello, this is a sample PDF document) Tj
ET
endstream
endobj
xref
0 6
0000000000 65535 f 
0000000010 00000 n 
0000000055 00000 n 
0000000110 00000 n 
0000000214 00000 n 
0000000262 00000 n 
trailer
<< /Size 6
   /Root 1 0 R
   /Info 2 0 R
>>
startxref
370
%%EOF
```

When sending PDFs through HTTP, set the content-type header as application/pdf and put the pdf file as the payload.
Example in Next JS:
#nextjs 
```js
import { PDFDocument } from 'pdf-lib'

export async function GET(Request) {

    const pdfDoc = await PDFDocument.create()
    const page = pdfDoc.addPage()
    page.drawText('You can create PDFs!')
    // const pdfBytes = await pdfDoc.save()

    // const pdfDoc = await PDFDocument.create();
    const page1 = pdfDoc.addPage();
    page1.moveTo(110, 200);
    page1.drawText('Hello World!');
    const pdfDataUri = await pdfDoc.save();

    return new Response(pdfDataUri, {
        status: 200,
        headers: { 'content-type': 'application/pdf' }
    });
}
```