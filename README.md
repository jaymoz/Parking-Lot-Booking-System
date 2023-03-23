# PARKING LOT SPACE BOOKING SYSTEM

## Task description
Technical task

Build an API for booking parking spaces in the “Fregat office center”.
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

## NOTE:
- Two groups are available on creation
  - Manager
  - Employee
- By default all users on creation are added to the Employee group, only specific users are added to the Manager group which has special permissions
- Every User on creation is assigned a Token which can be used to make api calls to the database, authentication e.t.c.

- Manager:
 - can add, delete and edit information about booked time of the parking space.
 - can add, delete and edit information about Parking spaces.
 
- Employee
 - Can reserve a parking space for a specified time.

# Database structure
There are two main models in the database:

- Parking Space
  - park_name: This describes the name of the park where users can book spaces.
  - no_of_spaces: The number of spaces available in the park(default number for each park is 2 as per task description).

- Bookings
   - owner: Name of the user who placed a booking
   - manufacturer: describes information about the make of the vehicle
   - car_model: describes information about the vehicle model
   - plate_number: vehicle plate number
   - start_period: date and time at which vehicles can be parked
   - end_period: date and time at which booking expires and vehices must be removed
   - is_booked: Shows that booking was succesful and is valid( NOTE: Bookings are not deleted from the database but are flagged to false which shows the booking has been cancelled)
   - ticket: booking ticket which give you entrance to park vehicle
   - phone: User mobile number
   - parking_space: Name of parking space where user can park the vehicle
 
 # Bookings are not deleted from the database rather the "is_flagged" field in "Bookings" is set false which shows the booking has been cancelled or has expired.This is because booking details are important and should be treated as such!
 
 - to use the application it is necassary to first create a parking space!!!
 

# API DOCUMENTATION
Using the website replace the local host with http://jaymoz.pythonanywhere.com/api/[path]
e.g:
   http://jaymoz.pythonanywhere.com/api/create-parking-space/

 - id-booking: unique id of each succesful booking placed.
 - id-park-to-book: unique if of the intended parking space where you want to book.


- Get user Token:
```html
   sudo install httpie
   http POST  http://127.0.0.1:8000/api-token-auth/ username=“YOUR_USERNAME" password=“YOUR_PASSWORD”
```
Create a Parking Space (only for users in Manager group):
- url: 
```
   http://127.0.0.1:8000/api/create-parking-space/
  ```
View all parking spaces:
- url: 
```
   http://127.0.0.1:8000/api/parking-spaces/
  ```
Delete a parking space (only for users in Manager group):
- url: 
```
   http://127.0.0.1:8000/delete-parking-space/[id-parking-space]/
  ```
View all bookings (only users in Manager group can view all bookings, users in Employee groups can see only their bookings):
- url: 
```
   http://127.0.0.1:8000/bookings/
  ```
Book a parking space:
- url: 
```
   http://127.0.0.1:8000/api/book/[id-park-to-book]/
  ```
Update a parking space:
- url: 
```
   http://127.0.0.1:8000/api/update-parking-space/[id-park-to-book]/
  ```
update booking (only for users in Manager group):
- url: 
```
   http://127.0.0.1:8000/api/update-booking/[id-booking]/
  ```
cancel a booking (only for users in Manager group):
- url: 
```
   http://127.0.0.1:8000/api/cancel-booking/[id-booking]/
  ```
View booking details:
- url: 
```
   http://127.0.0.1:8000/api/booking-detail/[id-booking]/
  ```
