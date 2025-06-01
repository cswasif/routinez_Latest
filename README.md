# RoutinEZ - USIS Course Management System

RoutinEZ is a comprehensive web application designed to simplify course management and routine generation for students. It consists of a frontend web interface and a backend API.

**Frontend:** Built with React.js, it provides a user-friendly interface for interacting with the backend, allowing you to search for courses, view seat status, select your preferences, and generate your routine.

**Backend:** Built with Python and Flask, the backend API is structured as a serverless function for deployment on platforms like Vercel. It fetches and processes course data, including seat availability, schedules, and exam dates. It also houses the routine generation logic, including the AI component.

## Features

RoutinEZ offers the following key features:

### Seat Status
-   **Real-time Data:** Check the current seat availability for any course.
-   **Detailed Course Information:** View detailed schedules (class and lab), assigned faculty, room information, and exam dates (midterm and final) for each section.
-   **Faculty Breakdown:** See how sections and available seats are distributed among different faculty members teaching a course.

### Routine Generation
-   **Flexible Input:** Easily select your desired courses, preferred faculty members, available days of the week, and time slots using intuitive input fields with autocomplete and tagging.
-   **AI-Powered Optimization:** Leverage the power of AI to generate a routine that attempts to optimize based on your preferences and a chosen commute style (living near or far from campus).
-   **Manual Control:** If you prefer, you can generate routines without the AI, based purely on your selected courses, faculty, days, and times.
-   **Conflict Detection:** The system automatically identifies and reports potential conflicts in your generated routine, including overlapping class/lab times and conflicting exam schedules.
-   **PNG Export:** Download your generated routine as a shareable image file.

## How AI is Used

The AI in RoutinEZ is specifically designed to assist in generating a better routine based on your input. When you choose to "Use AI for Best Routine," the system sends your selected courses, preferred faculty, available days, times, and commute preference to the backend. The AI algorithm then processes this information, considering factors like minimizing travel time (based on commute preference) and optimizing the distribution of classes, to propose a routine that best fits your criteria while avoiding conflicts.

## How Faculty Information is Used

Faculty information plays a crucial role in both the Seat Status and Routine Generation features:

-   **Seat Status:** In the Seat Status view, you can see which faculty members are teaching each section and the availability of seats within those sections taught by specific faculty. This helps you make informed decisions based on instructor preferences.
-   **Routine Generation:** When generating a routine, you have the option to specify preferred faculty members for the courses you select. The routine generation logic (both manual and AI-powered) takes your faculty preferences into account when searching for available sections, prioritizing sections taught by your chosen instructors where possible.

## Tech Stack

### Frontend
-   React.js
-   Axios for API calls
-   Date-fns for date formatting
-   Html2canvas for routine export
-   Custom components and inline styling for a minimal and modern look

### Backend
-   Python
-   Flask
-   RESTful API architecture
-   AI/Optimization logic (implemented in Python)
-   Data parsing and handling

## Installation

These instructions are for setting up the project for **local development**.

### Prerequisites
-   Node.js (v14 or higher)
-   Python 3.8 or higher
-   npm or yarn

### Backend Setup (Vercel Structure Local Test)

1.  Navigate to the root of the repository:
    ```bash
    cd path/to/RoutinEZ
    ```

2.  Install Python dependencies for the Vercel backend:
    ```bash
    pip install -r api/requirements.txt
    ```

3.  If your backend requires environment variables (like `GOOGLE_API_KEY`), create a `.env` file at the root of the repository.

4.  Run the Vercel backend serverless function locally (requires `python-dotenv` if using .env):
    ```bash
    python api/usisvercel.py
    ```
    The server will run on `http://localhost:5000`.

### Frontend Setup
1.  Navigate to the frontend directory:
    ```bash
    cd USIS/usis-frontend
    ```

2.  Install dependencies:
    ```bash
    npm install
    ```

3.  Start the development server:
    ```bash
    npm start
    ```
    The application will open in your browser at `http://localhost:3000`

## Usage

Detailed usage instructions are provided within the application interface itself. Simply open the application in your browser and follow the prompts to check seat status or generate your routine.

## API Endpoints

### Courses
-   `GET /api/courses` - Get all available courses
-   `GET /api/course_details?course={code}` - Get detailed course information

### Routine
-   `POST /api/routine` - Generate routine with parameters:

    ```json
    {
      "courses": [
        {
          "course": "CSE101",
          "faculty": ["John Doe"],
          "sections": {
            "John Doe": "A"
          }
        }
      ],
      "days": ["Monday", "Wednesday"],
      "times": ["8:00 AM-9:20 AM"],
      "useAI": true,
      "commutePreference": "far"
    }
    ```

## Project Structure

This project follows a standard structure suitable for Vercel deployment:

```
RoutinEZ/
├── api/                     # Contains Vercel Serverless Functions (Python)
│   ├── requirements.txt     # Python dependencies for serverless function
│   └── usisvercel.py        # Main backend serverless function (Flask application)
├── USIS/
│   └── usis-frontend/       # React frontend application
│       ├── public/          # Static assets
│       ├── src/             # Frontend source code
│       │   ├── components/  # Reusable React components
│       │   │   ├── ui/      # UI components (e.g., waves, grid)
│       │   │   └── ...      # Other components
│       │   ├── App.js       # Main application component and core logic
│       │   ├── App.css      # Main application styles
│       │   └── index.js     # Application entry point
│       └── package.json     # Frontend dependencies and scripts
├── .gitignore              # Specifies intentionally untracked files
├── LICENSE                 # Project license
├── README.md               # Project documentation (this file)
└── vercel.json             # Vercel configuration for routing serverless functions
```

## Vercel Deployment

This project is configured for easy deployment on Vercel. The `vercel.json` file at the root of the repository specifies how incoming requests are handled.

-   The `rewrites` rule in `vercel.json` routes all requests to `/api/*` to the `api/usisvercel.py` serverless function.
-   Vercel automatically detects the React application in the `USIS/usis-frontend` directory and builds/serves it as the frontend.

To deploy to Vercel:

1.  Push your changes to the `main` branch of your connected GitHub repository.
2.  Vercel will automatically detect the push and trigger a new build and deployment.
3.  Once the deployment is complete, your application will be live at your Vercel project URL.

### 🚨 Important: Clear Browser Cache After Deployment

After a new Vercel deployment, it is **highly recommended** to clear your browser's cache and cookies for the application's URL. This ensures that your browser loads the latest version of the frontend code, which is crucial for seeing recent changes and avoiding issues like outdated API endpoints being called.

## Contributing

Contributions are welcome! Please follow these steps:

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

-   Based on the USIS course data structure.
-   Utilizes open-source libraries like React, Flask, Axios, date-fns, and html2canvas.

## Contact

For any questions, issues, or feedback, please open an issue on the GitHub repository.

## Future Enhancements

-   [ ] Dark mode support
-   [ ] Mobile responsiveness improvements
-   [ ] More advanced conflict resolution algorithms
-   [ ] Integration of course prerequisites checking
-   [ ] Analysis of GPA impact based on routine choices
-   [ ] Export routine to other formats (e.g., PDF, iCal)
-   [ ] Multi-language support 