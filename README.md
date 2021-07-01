# Documentation for Invoice-Gen • 인보이스-젠 문서 매뉴얼

## Brief Introduction

This C++ desktop application takes user inputs via GUI forms and creates a pdf file.
It contains an invoice with a specific format. The format of the invoice follows the Czech business standards. The project is made primarily for my parents’ accommodation business.

해당 어플리케이션은 GUI 폼 요소를 통해 유저 입력값으로 PDF 파일을 만듭니다. 이 PDF 파일은 특정한 인보이스 형식을 따릅니다. 인보이스 형식은 체코 공화국의 사업적 기준에 맞추어져 있습니다.

## Design

The application takes several user inputs in form of strings.
The inputs are stored in entities/objects.

Entities:

- Invoice
    - invoice number
    - issue date
    - VAT date
    - due date
    - supplier
    - supplier bank
    - customer
    - item list
    - exchange


- Person (Supplier/Customer)
    - name
    - company
    - address [street, zip, city/district]
    - country
    - ID number (business registry)
    - VAT number
    - phone number
    - mobile number
    - email address
    - bank
    - logo (image)
    - METHODS
        - calculateExchange
        - getDate

- Bank
    - bank name
    - account holder
    - international or domestic
    - IBAN code or account number
    - SWIFT code
    - reference number
    - METHODS
        - checkType: updates the forms to either international or domestic

- Item
    - description
    - quantity
    - service start (dd.mm.yyyy)
    - service end (dd.mm.yyyy)
    - single price
    - VAT rate
    - VAT already included in price (yes or no)
    - METHODS
        - checkIncluded:
            ```
            if (VAT already included in price) is true:
                returns (single price) * (quantity)
            else
                returns ((single price) + (rate * single price)) * (quantity)
            ```
        - getDate

- Exchange
    - initial amount
    - from
    - to
    - rate
    - date exchanged
    - exchange institute
    - METHODS
        - calculateExchange
        - getDate

- other forms in strings / non-class variables
    - issuer
    - person confirming
    - date received

Once the inputs are all given, the application processes some calculations for the item prices, VAT information and the exchange amount. Then it produces a pdf file from the strings. The application requests the user to save the pdf file on the device.
