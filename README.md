# Interview Practical
 intern interview 

# Part 1 Backend

Setting Up Laravel Project and Creating Client Model:

Install Laravel using Composer:

composer create-project --prefer-dist laravel/laravel project-name

Step 2
Create a Client model with required fields:

php artisan make:model Client -m

Step 3
Define fields like name, gender, dob, marital_status, and approval_status in the migration file generated.
Implementing Routes and Controller Methods:

Step 4
Define routes in routes/api.php for CRUD operations:

Route::post('/clients', 'ClientController@store');
Route::get('/clients/{id}', 'ClientController@show');
Route::put('/clients/{id}', 'ClientController@update');
Route::delete('/clients/{id}', 'ClientController@destroy');
Route::patch('/clients/{id}/approve', 'ClientController@approve');
Route::patch('/clients/{id}/withdraw-approval', 'ClientController@withdrawApproval');

Step 5
Implement controller methods in app/Http/Controllers/ClientController.php for each route:

public function store(Request $request) { ... }
public function show($id) { ... }
public function update(Request $request, $id) { ... }
public function destroy($id) { ... }
public function approve($id) { ... }
public function withdrawApproval($id) { ... }

Step 6
Implementing Authentication Middleware:

Generate authentication using Laravel's built-in authentication scaffolding:

php artisan make:auth
Use Laravel Passport or Sanctum for API token authentication.

Step 7
Apply authentication middleware to routes in routes/api.php:

Route::middleware('auth:api')->group(function () {
    // CRUD routes here
});
Implementing Validation Middleware:

Create a new middleware for data validation:
php artisan make:middleware ValidateClientData
Implement validation logic in the middleware to ensure incoming data meets required criteria (e.g., using Laravel's validation rules).
Apply the validation middleware to appropriate routes in routes/api.php:

Route::post('/clients', 'ClientController@store')->middleware('validate.client.data');
Route::put('/clients/{id}', 'ClientController@update')->middleware('validate.client.data');
By following these steps, you'll have successfully created a RESTful API in Laravel for managing clients, complete with authentication and validation functionalities.

 
# Part 2 Front End

The Steps Followed
Step 1

Setting Up Angular Project:

Install Angular CLI globally if not already installed:
npm install -g @angular/cli
Create a new Angular project:
ng new project-name
Navigate into the project directory:
cd project-name

Step 2
Developing a Component to Display a Table of Clients:

Generate a new component to display the clients table:

ng generate component client-table

Step 3
Fetching List of Clients from RESTful API:

Install HttpClientModule for making HTTP requests:
ng add @angular/common
Inject HttpClient into the client-table component to fetch data from the API.
Make a GET request to the Laravel API endpoint to fetch the list of clients.

Step 4
Displaying Client Details in Table Format:

Use Angular Material Table or another UI library to display data in a tabular format.
Bind the fetched client data to the table rows and columns.
Including a Button to Approve a Client:
Add a button or action column in the table to approve a client.
Implement a click event handler to trigger the approval functionality.

Step 5
Implementing Functionality to Update Approval Status:
Utilize HttpClient to make a PATCH or PUT request to the Laravel API endpoint to update the approval status of a client.
Implement the logic to send the request when the approve button is clicked.
Handling Validation of Data Received from API:

Step 6
Implement error handling in the client-table component to handle validation errors or inconsistencies in the data received from the Laravel API.
Display error messages or handle errors gracefully to ensure a smooth user experience.
