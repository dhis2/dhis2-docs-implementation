# Consignment receipt acknowledgement / Tracker program

## Introduction

This very simple Event program allows users at healthcare facilities to acknowledge receipt of consignments on a mobile device by scanning any type of barcode printed on the packing list. The configuration includes the option of signing on the screen of the mobile device, recording the geolocation of receipt and taking an image but additional features can be added as needed.

## Use case

The medical store which supplies the respective healthcare facility processes the order, picks, packs and ships the consignment with a packing list with a barcode indicating the consignment identification printed on it. The storekeeper receives, unloads, checks the consignment and acknowledges receipt by scanning the barcode and completing the Event Program form with additional information such as the geolocation of the mobile device used, signing on the screen and taking an image of the consignment, for example in front of the healthcare facility or in the pharmacy. After synchronising the Capture Android app, all these details are synchronised with the central DHIS2 instance and available to any DHIS2 user in the country.
The information can be used simply to allow supply managers to keep track for which consignments delivery was confirmed and for which they are still pending.
When using the DHIS2-RTS (Real-Time Stock management system), the acknowledgement of receipt 

## Maintenance Web App - DHIS2 metadata configuration

This application is configured as an "Event program" which uses only simple, native DHIS2 functionality and can be easily customized and adapted to specific needs and use cases.
The barcode field can be configured as a simple linear barcode a QR-code or a GS1 DataMatrix code depending on what type of barcode is being printed on the packing list.

### Metadata overview
>**1 DATA ELEMENT**  
>>1.1 Data element - "Tracker"  
> 
>**2 ORGANISATION UNIT**  
>>2.1 Organisation unit  
> 
>**3 PROGRAM**  
>>3.1 Program  

### 1 DATA ELEMENT
#### 1.1 Data element - "Tracker"  
>**Name**
>>"Consignment number" / "Text"  
>>"Recipient signature" / "Image"  
>>"Receipt geolocation" / "Coordinate"   
>>"Receipt image" / "Image" 
>
>**Short name \(*)**: same as "Name (\*)"   
>**Domain Type \(*)**: "Tracker"  
>**Value type \(*)**: see above (entry next to the respective name)
>**Aggregation type (*)**: "None"


### 2 ORGANISATION UNIT
#### 2.1 Organisation Unit
The Organisation Unit, Organisation Unit group and Organisation Unit level are created and added according to national protocols and policies and/or existing DHIS2 configuration and there are no specific requirements for using the Consignment receipt acknowledgement program.

### 3 PROGRAM
The DHIS2 Event Program, which lies at the core of the DHIS2-RTS application, is very simple to configure, uses only native DHIS2 functionality and governs the customized user interface on the mobile device.

#### 3.1 Program
>**1 Program details**
>>**Name \(*)**: "Consignment receipt acknowledgement"  
>>**Short name (*)**: "Consignment receipt acknowledgement"  
>>**Color**: "#006064"  
>>**Icon**: "stock out outline"  
>>**Description**: "Event for receiving medical consignment at health facility"  
>>**Version**: (automatically numbered by the system)
>>**Category combination (*)**: select "None"  
>>**Expiry days**: "0"  
>>**Pre-generate event UID**: tag  (appears as white tick in a blue square)
>
>**2 Assign data elements**  
>>**Search available/selected items**: select and arrange in the following order:
>>>"Consignment number"  
>>>"Recipient signature"  
>>>"Receipt geolocation"  
>>>"Receipt image"  
>>**Display in reports**: tag all  
>>**Mobile render type**: "Default"
>>>"Consignment number": "Qr code" ("Bar code" or "Gs1 datamatrix" depending on what type of barcode is used).
>>>"Recipient signature": "Canvas"
>>>"Receipt geolocation": "Default"
>>>"Receipt image": "Default"
>
>**3 Create data entry form**
>>**"BASIC"** (configured by the system by default, no configuration is needed)
>>>"Consignment number"
>>>"Recipient signature"
>>>"Receipt geolocation"
>>>"Receipt image"
>
>**5 Access**
>>**Organisation units**: tag the health care facilities where the Tracker Program is used  
>>**Roles and access**: "Biomedical equipment life cycle management" appears by default  
>>>**Consignment receipt acknowledgement**: tag  
>
>**6 Notifications**  
>(not applicable)

