# 🎓 Course Enrollment System

An **ASP.NET Core MVC web application** that allows students to browse online courses, calculate discounted tuition fees, view course details, and enroll using their contact information. The application demonstrates session management, cookies, caching, query strings, and asynchronous API integration.

## ✨ Features

- **Course Catalog:** Browse available courses with course duration, original fees, discount percentages, and final fees.
- **Course Details:** View detailed information about a selected course using the `courseId` query string.
- **Course Enrollment:** Submit an enrollment form with student name and email.
- **My Course:** Revisit the course selected during the current session.
- **Student Information:** Store student name and email in browser cookies and display them on the confirmation and My Course pages.
- **Learner Directory:** Retrieve learner information, including names, email addresses, and company details, asynchronously from JSONPlaceholder.
- **Discount Calculation:** Automatically calculate final course fees based on the listed price and discount percentage.
- **Session Management:** Maintain the selected course using ASP.NET Core session state.
- **Caching:** Cache the course catalog using `IMemoryCache` for five minutes and enable response caching for course details.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| C# | Application programming language |
| ASP.NET Core MVC | Web application framework |
| .NET 10 | Runtime and SDK |
| Razor Views | Dynamic HTML rendering |
| IMemoryCache | In-memory course catalog caching |
| Session State | Maintain the selected course |
| Cookies | Store student contact details |
| Response Caching | Improve response efficiency |
| JSONPlaceholder API | Retrieve learner directory data |
| HTML and CSS | User interface and styling |

## 📋 Prerequisites

Before running the application, make sure you have:

- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)
- A code editor such as [Visual Studio](https://visualstudio.microsoft.com/) or [Visual Studio Code](https://code.visualstudio.com/)
- Internet access to retrieve learner data from JSONPlaceholder

Verify your .NET installation:

```bash
dotnet --version
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Navigate to the project directory

```bash
cd <YOUR_PROJECT_DIRECTORY>
```

### 3. Restore dependencies

```bash
dotnet restore
```

### 4. Run the application

```bash
dotnet run
```

### 5. Open the application

Open the local URL printed in your terminal. The configured launch profile uses:

**http://localhost:5182**

If the application starts on a different port, use the URL displayed by `dotnet run`.

## 🌐 Application Routes

| Route | Description |
|---|---|
| `/Course` | Displays the course catalog and learner directory |
| `/Course/Details?courseId=1` | Displays details for the course with ID 1 |
| `/Course/MyCourse` | Displays the course selected during the current session |

## 💰 Course Fee Calculation

The application calculates the final tuition fee by applying the course's discount percentage to its original listed fee.

**Formula:**

```text
Discount Amount = Original Fee × Discount Percentage / 100

Final Fee = Original Fee - Discount Amount
```

The `CalculateFinalFees()` method performs this calculation.

**Example:**

For a course with an original fee of ₹10,000 and a discount of 20%:

- Original Fee: ₹10,000
- Discount: 20%
- Discount Amount: ₹2,000
- **Final Fee: ₹8,000**

## 🔄 State Management

The project demonstrates different approaches to maintaining and transferring application data.

| Mechanism | Usage |
|---|---|
| Cookies | Store the enrolled student's name and email |
| Session | Store the selected course for the current session |
| Query String | Pass the course ID to the course details page |
| Hidden Form Field | Submit the enrollment course ID with the form |
| IMemoryCache | Cache the course catalog for five minutes |
| Response Caching | Enable caching for course detail responses |

## 👨‍🎓 Learner Directory API

The application retrieves learner information asynchronously from JSONPlaceholder.

**API endpoint:**

https://jsonplaceholder.typicode.com/users

The directory uses the API's sample user data to display information such as:

- Student or learner name
- Email address
- Company name

An active internet connection is required for this feature.

## 📂 Project Structure

The application follows the ASP.NET Core MVC architectural pattern.

```text
CourseEnrollmentSystem/
│
├── Controllers/
│   └── CourseController.cs
│
├── Models/
│   └── Course.cs
│
├── Views/
│   └── Course/
│       ├── Index.cshtml
│       ├── Details.cshtml
│       ├── MyCourse.cshtml
│       └── ...
│
├── wwwroot/
│   ├── css/
│   ├── js/
│   └── ...
│
├── Properties/
│   └── launchSettings.json
│
├── Program.cs
├── appsettings.json
└── README.md
```

*Note: This is a representative structure. Update the file and folder names to match your actual project.*

## 🧪 Testing the Application

1. Run the application using `dotnet run`.
2. Open `/Course` and browse the available courses.
3. Verify that the original fees, discounts, and final fees are displayed correctly.
4. Open a course using its `courseId` query string.
5. Submit the enrollment form with a student's name and email.
6. Visit `/Course/MyCourse`
