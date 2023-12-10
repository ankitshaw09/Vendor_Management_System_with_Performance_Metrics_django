# Django Vendor Management System

A Vendor Management System (VMS) built using Django and Django REST Framework. This system manages vendor profiles, tracks purchase orders, and calculates vendor performance metrics.

## Table of Contents

- [Features](#features)
- [Technical Requirements](#technical-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)

## Features

1. **Vendor Profile Management:**
   - Create, retrieve, update, and delete vendor profiles.
   - Calculate and display vendor performance metrics.

2. **Purchase Order Tracking:**
   - Create, retrieve, update, and delete purchase orders.
   - Track delivery status, items, quantity, and other details.

3. **Vendor Performance Evaluation:**
   - Calculate performance metrics, including on-time delivery rate, quality rating average, average response time, and fulfillment rate.
   - Historical performance tracking for trend analysis.

## Technical Requirements

- Django (latest stable version)
- Django REST Framework (latest stable version)
- Token-based authentication
- PEP 8 compliant code
- Comprehensive data validations
- Django ORM for database interactions

## Installation

2. Create and activate a virtual environment:
    ```bash
    python -m venv venv
    .\venv\Scripts\activate

   
2. Install dependencies:
   ```bash
    pip install -r requirements.txt

3. Run migrations:
    ```bash 
    python manage.py makemigrations
    python manage.py migrate
4. Run :
    ```bash 
    python manage.py runserver

## API 

    ```bash 
    http://127.0.0.1:8000/admin/
    http://127.0.0.1:8000/api/vendors/ 
    http://127.0.0.1:8000/api/vendors/<int:pk>/ 
    http://127.0.0.1:8000/api/purchase_orders/
    http://127.0.0.1:8000/api/purchase_orders/<int:pk>/ 
    http://127.0.0.1:8000/api/historical_performance/ 
    http://127.0.0.1:8000/api/vendors/<int:vendor_id>/performance/ 
    http://127.0.0.1:8000/api/purchase_orders/<int:pk>/acknowledge/ 


5.  ## API Documentation
    Detailed API documentation is available in the [API Documentation](api_documentation.md) file. Please refer to this documentation for detailed information about each API endpoint, including input parameters, authentication requirements, and response formats.



  

    ```bash
    Sample JSON for Creating a New Vendor
    {
    "name": "Sample Vendor",
    "contact_details": "123-456-7890",
    "address": "456 Main St, City",
    "vendor_code": "SAMPLE123",
    "on_time_delivery_rate": 95.0,
    "quality_rating_avg": 4.5,
    "average_response_time": 2.5,
    "fulfillment_rate": 98.0
    }

    Sample JSON for Acknowledging a Purchase Order Create a file named acknowledge_purchase_order.json with the following content:

    json  

    {
    "acknowledgment_date": "2023-12-10T12:00:00"
    }

5.  ## Vendor Endpoints
    
    1.  Create a new vendor:
    
        URL: POST /api/vendors/
            Payload Example:
            
                json
                {
                    "name": "Vendor Name",
                    "contact_details": "Contact Information",
                    "address": "Vendor Address",
                    "vendor_code": "ABC123"
                }
        *Authentication: Token-based authentication required.
    
    2.  List all vendors:

            URL: GET /api/vendors/
            Authentication: Token-based authentication required.
            Retrieve a specific vendor's details:

            URL: GET /api/vendors/{vendor_id}/
            Authentication: Token-based authentication required.
            Update a vendor's details:

            URL: PUT /api/vendors/{vendor_id}/
            Payload Example:

            json
             
            {
            "name": "Updated Vendor Name",
            "contact_details": "Updated Contact Information",
            "address": "Updated Vendor Address",
            "vendor_code": "ABC123"
            }

        *Authentication: Token-based authentication required.
            
            Delete a vendor:

            URL: DELETE /api/vendors/{vendor_id}/
            Authentication: Token-based authentication required.
            Retrieve a vendor's performance metrics:

            URL: GET /api/vendors/{vendor_id}/performance/
            Authentication: Token-based authentication required.
    
    3.  Purchase Order Endpoints

        Create a new purchase order:

            URL: POST /api/purchase_orders/
            
            Payload Example:
            json
            
            {
            "po_number": "PO123",
            "vendor": 1,
            "order_date": "2023-12-10T10:00:00",
            "delivery_date": "2023-12-20T10:00:00",
            "items": [{"name": "Item1", "quantity": 10}],
            "quantity": 10,
            "status": "pending"
            }
            
        *Authentication: Token-based authentication required.
            
            List all purchase orders:

            URL: GET /api/purchase_orders/
            Authentication: Token-based authentication required.
            Retrieve details of a specific purchase order:

            URL: GET /api/purchase_orders/{po_id}/
            Authentication: Token-based authentication required.
            Update a purchase order:

            URL: PUT /api/purchase_orders/{po_id}/
            Payload Example:
            
            json
            {
            "status": "completed",
            "acknowledgment_date": "2023-12-12T10:00:00"
            }
        *Authentication: Token-based authentication required.
         
         Delete a purchase order:
            
            URL: DELETE /api/purchase_orders/{po_id}/
        *Authentication: Token-based authentication required.
            
            Acknowledge Purchase Order Endpoint
            Acknowledge a purchase order:
            URL: PATCH /api/purchase_orders/{po_id}/acknowledge/
            Payload Example:
            
            json
            {
            "acknowledgment_date": "2023-12-12T10:00:00"
            }
        *Authentication: Token-based authentication required.
            Please note that you should replace {vendor_id} and {po_id} in the URLs with the actual vendor and purchase order IDs you want to interact with.

            Ensure you have the appropriate authentication token and include it in the request headers for endpoints that require authentication. Also, adjust the payload examples based on the actual structure and requirements of your Django application.






