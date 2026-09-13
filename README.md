# Personal Form Landing Page

This project is a single-page, mobile-friendly website made as a playful and expressive online form. The page is designed to present a personal introduction, collect a set of structured answers, and send the result through a static form submission flow.

## What this project is

This is not a tutorial project or a starter template. It is a complete front-end experience built for a specific purpose: to create an engaging digital form that feels personal, modern, and memorable while still being lightweight and easy to deploy.

The website combines:

- a strong visual identity with bold typography and colorful accents
- a custom form with multiple question types
- client-side validation and feedback states
- a compact structure without external build tooling
- a static deployment model suitable for hosting on simple web services

## Purpose of the project

The main idea is to give someone a clean way to present themselves through a visual landing page and a structured questionnaire. Instead of a plain text form, this project turns the interaction into a more intentional experience with personality, layout, and flow.

It is designed to feel like a modern personal web page where a visitor can:

- read a short introduction
- fill in a set of personal details
- answer availability and preference questions
- submit the form and trigger an email-based response workflow

## Project structure

- `index.html` — the main website including HTML, CSS, and JavaScript in one file
- `PETUNJUK.md` — internal notes and implementation details for local setup and behavior
- `README.md` — public overview of the project

## Key features

- Responsive layout optimized for mobile devices first
- One-file implementation for simplicity and portability
- Custom validation for required answers and form logic
- Availability selector with time-range handling
- Inline feedback for failed or successful submission attempts
- Styling built with no framework dependency

## Why this project was built this way

This project is intentionally lightweight. Everything is kept in a single HTML file so it is:

- easy to move around
- easy to host without a backend
- easy to edit for quick changes
- simple to understand for someone checking the code directly

The design aims to balance personality and usability: it feels less like a generic form and more like a crafted landing page with a clear goal and a memorable presentation.

## How it works

The page loads as a regular website and presents a form built for a specific interaction. Users fill out the fields, the frontend validates the input, and once the form is submitted, the data is sent through a static form endpoint and processed by the chosen email service.

The logic includes:

- required field checks
- character limits
- conditional availability modes
- time validation and summary display
- user-friendly error messages
- distinct success and failure states

## What makes it different

This project stands out because it is not just a form; it is a themed experience. The page is built to be expressive and memorable while still remaining functional. It blends visual storytelling with practical form mechanics in a way that feels more personal than a typical business form.

## Use case

This project is suitable for scenarios where a person wants to share a short personal introduction and collect responses in a structured, visually appealing way without setting up a large application.

Examples include:

- personal web pages
- creative proposal or introduction forms
- one-page contact or interest forms
- lightweight interactive landing pages

## Notes

The repository is focused on the frontend experience rather than a full application backend. That means the project is intentionally simple, but it is still a real, usable web page designed to serve a specific purpose rather than being a generic starting point.

## License

This project is shared as a personal web project and can be adapted for similar use cases. Please review the hosting and form-service configuration before publishing it publicly.
