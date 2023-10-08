# Release Notes

This page provides an overview of the changes made in each version of the Document Forensics project, including new features, improvements, and bug fixes.

## Version History

### [v1.2.0] - 2023-10-06
#### New Features:
- Introduced API endpoints for forensic analysis.
- Added Gradio UI for easier interaction.
- Enhanced inpainting detection algorithms.

#### Improvements:
- Improved performance and speed of the splicing detection.
- Optimized the project setup using Docker and Docker Compose.

#### Bug Fixes:
- Fixed an issue where the erasing detection was not accurate in certain cases.
- Addressed a bug that caused incorrect labeling in the Copy-Move detection.

### [v1.1.0] - 2023-08-15
#### New Features:
- Added support for more image formats including 'webp'.
- Introduced a new setup script for easier deployment.

#### Improvements:
- Enhanced the accuracy of the Copy-Move detection.
- Improved the documentation for better understanding of the setup process.

#### Bug Fixes:
- Fixed a bug that caused the project to fail when processing large images.
- Addressed an issue where the Docker container would not start due to missing dependencies.

### [v1.0.0] - 2023-02-17
#### New Features:
- Initial release with basic forensic features including Copy-Move, Splicing, Erasing, Masking, and Inpainting detection.
- Provided Docker and Docker Compose setup for easy deployment.
