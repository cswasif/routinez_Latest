# RoutinEZ - USIS Course Management System

RoutinEZ is a comprehensive web application designed to simplify course management and routine generation for students. It provides real-time seat availability information and offers both manual and AI-powered tools to help you create an optimal class schedule.

## How it Works

RoutinEZ consists of two main parts: a backend API and a frontend web interface. The backend, built with Python and Flask, fetches and processes course data, including seat availability, schedules, and exam dates. It also houses the routine generation logic, including the AI component. The frontend, built with React.js, provides a user-friendly interface for interacting with the backend, allowing you to search for courses, view seat status, select your preferences, and generate your routine.

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

### Prerequisites
-   Node.js (v14 or higher)
-   Python 3.8 or higher
-   npm or yarn

### Backend Setup
1.  Navigate to the USIS directory:
    ```bash
    cd USIS
    ```

2.  Install Python dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3.  Start the backend server:
    ```bash
    python usis.py
    ```
    The server will run on `http://localhost:5000`

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

```
RoutinEZ/
├── USIS/
│   ├── usis.py              # Backend server (Python/Flask)
│   ├── requirements.txt     # Python dependencies
│   └── usis-frontend/       # React frontend application
│       ├── public/          # Static assets
│       ├── src/             # Frontend source code
│       │   ├── components/  # Reusable React components
│       │   │   ├── ui/      # UI components (e.g., waves, grid)
│       │   │   └── ...      # Other components (e.g., SeatStatusDialog)
│       │   ├── App.js       # Main application component and logic
│       │   ├── App.css      # Main application styles
│       │   └── index.js     # Application entry point
│       └── package.json     # Frontend dependencies and scripts
├── .gitignore              # Specifies intentionally untracked files
├── LICENSE                 # Project license
└── README.md               # Project documentation (this file)
```

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