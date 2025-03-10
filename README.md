# Emergency Health Card

Checkout the Website: https://emergency-health-card.vercel.app/
### Features

- User Authentication:
  - Secure user signup and login using email and password with hashed password storage.
  - Password reset functionality (simulated for now, can be extended with email integration).
  - Logout option to ensure session security.
- Health Card Management:
  - Create and store personal health details including name, age, blood group, emergency contacts, medications, allergies, and more.
  - Edit existing health cards with updated information and profile pictures.
  - Generate QR codes linking to individual health card data for quick access in emergencies.
- Data Accessibility:
  - Publicly accessible health card data via QR code scanning (no login required for viewing).
  - Secure dashboard for authenticated users to manage their health cards.
  - Support for multiple emergency contacts stored in JSON format for flexibility.
- User Interface:
  - Clean and responsive design for ease of use on desktop and mobile devices.
  - Intuitive forms for creating and editing health cards with clear input fields.
  - Visual feedback with QR code display after health card creation or update.
  
### Installation and Run Instructions
1. Clone the Repository:
`git clone https://github.com/your-username/emergency-health-card.git
cd emergency-health-card`
2. Set Up the Environment:
  - Ensure you have Python installed.
  - Install required dependencies:
  `pip install flask flask-login flask-bcrypt sqlite3 qrcode pillow`
3. Run the Application:
  - Start the Flask server:
  `python app.py`
  - Open your web browser and navigate to `http://localhost:5000`.
4. Usage:
  - Sign up or log in to access the dashboard.
  - Create a new health card by filling out the form and uploading a profile picture (optional).
  - Save the generated QR code for emergency use.
  - Edit existing health cards from the dashboard as needed.

### Interesting Parts during the Build Process
- QR Code Integration:
  - Generating QR codes dynamically with the qrcode library and linking them to user-specific URLs was a standout feature.
  - Ensuring the QR codes were stored efficiently and accessible via a public route added a practical real-world utility.
- Database Design:
  - Implementing a relational SQLite database with users_auth and users tables allowed for secure and scalable data management.
  - Adding support for JSON-encoded multiple emergency contacts was a creative solution to handle dynamic input fields.
- Flask-Login Integration:
  - Leveraging Flask-Login for session management and protecting routes made the authentication flow seamless and secure.

### Difficulties Faced and Solutions
- Multiple Emergency Contacts:
  - Challenge: Handling dynamic input for multiple emergency contacts in the form and storing them efficiently.
  - Solution: Used request.form.getlist() to capture multiple inputs and stored them as a JSON string in the database, maintaining backward compatibility with a single emergency_contact field.
- File Upload Handling:
  - Challenge: Securely managing profile picture uploads and associating them with users.
  - Solution: Created a dedicated static/uploads directory and named files with user_id prefixes to avoid conflicts, ensuring only authenticated users could upload.
- QR Code Accessibility:
  - Challenge: Making health card data accessible via QR codes without requiring login for emergency use.
  - Solution: Designed a public /user/<user_id> route that serves data without authentication, while keeping edit functionality behind login.
Capture screenshots of your dashboard and QR code page, upload them to your GitHub repository under the assets folder, and update the image paths in the README.
If you’ve deployed the app (e.g., via ngrok or a hosting service), you can add a "Live Demo" link under a new ## Live Demo section.
