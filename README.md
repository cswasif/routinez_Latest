# RoutinEZ - USIS Course Management System

RoutinEZ is a comprehensive course management system designed to help students manage their course schedules, check seat availability, and generate optimal class routines. The system provides both a user-friendly web interface and a robust backend API.

## Features

### Seat Status
- Real-time seat availability tracking
- Detailed section information
- Faculty-wise section distribution
- Exam schedule display
- Room allocation information

### Routine Generation
- AI-powered routine generation
- Manual routine generation
- Conflict detection (class, lab, and exam conflicts)
- Customizable day and time preferences
- Commute preference consideration
- Export routine as PNG

## Tech Stack

### Frontend
- React.js
- React Select for enhanced dropdowns
- HTML2Canvas for routine export
- Custom UI components with CSS animations

### Backend
- Python
- Flask
- RESTful API architecture
- JSON data handling

## Installation

### Prerequisites
- Node.js (v14 or higher)
- Python 3.8 or higher
- npm or yarn

### Backend Setup
1. Navigate to the USIS directory:
   ```bash
   cd USIS
   ```

2. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Start the backend server:
   ```bash
   python usis.py
   ```
   The server will run on http://localhost:5000

### Frontend Setup
1. Navigate to the frontend directory:
   ```bash
   cd USIS/usis-frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```
   The application will open in your browser at http://localhost:3000

## Usage

### Seat Status
1. Select a course from the dropdown
2. View available sections with:
   - Seat availability
   - Faculty information
   - Class schedule
   - Lab schedule
   - Exam dates

### Routine Generation
1. Select courses you want to take
2. Choose preferred faculty members
3. Select available days
4. Choose time slots
5. Set commute preference
6. Generate routine using either:
   - Regular generation
   - AI-powered generation

## API Endpoints

### Courses
- `GET /api/courses` - Get all available courses
- `GET /api/course_details?course={code}` - Get detailed course information

### Routine
- `POST /api/routine` - Generate routine with parameters:
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
│   ├── usis.py              # Backend server
│   ├── requirements.txt     # Python dependencies
│   └── usis-frontend/       # React frontend
│       ├── public/          # Static files
│       ├── src/             # Source code
│       │   ├── components/  # React components
│       │   ├── App.js       # Main application
│       │   └── index.js     # Entry point
│       └── package.json     # Node dependencies
└── README.md               # Documentation
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- USIS for course data structure
- React community for UI components
- Python Flask for backend framework

## Contact

For any queries or support, please open an issue in the GitHub repository.

## Future Enhancements

- [ ] Dark mode support
- [ ] Mobile responsiveness improvements
- [ ] Advanced conflict resolution
- [ ] Course prerequisites checking
- [ ] GPA impact analysis
- [ ] Export to PDF functionality
- [ ] Multi-language support 