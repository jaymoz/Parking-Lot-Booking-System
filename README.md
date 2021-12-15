# PARKING LOT SPACE BOOKING SYSTEM
## Task description
Technical task

Develop an application for booking parking spaces in the “Fregat office center”.
The application must have two employee roles: "Manager", "Employee".
- The manager can add, delete and edit information about booked time of the parking space.
- Employees must be able to reserve a parking space for the specified time.

List of required screens:
- Login to the application by login and password
- List of parking spaces (2 spaces)
- Adding / Changing Reservation time
- Adding / Deleting a parking space

Technologies used in this Task
- Django, Django Rest Framework

## installation and Api documentation
Clone this repo:
```
   git clone https://github.com/jaymoz/Parking-Lot-Booking-System.git
```
Open the folder in a code editor, create and activate a virtual environment and install dependencies (note: for mac os users):
```
   python3 -m venv nameofyourenv
   source nameofyourenv/bin/activate
   pip3 install -r requirements.txt 
```
Create database and make migrations:
```python
   python3 manage.py makemigrations
   python3 manage.py migrate
```
Create a superuser to gain access to the database:
```python
   python3 manage.py createsuperuser
```
run the server:
```python
   python3 manage.py runserver
```
