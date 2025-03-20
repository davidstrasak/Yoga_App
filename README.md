# Yoga App

A distraction-free mobile application for your daily yoga practice. This app provides a curated selection of yoga videos without YouTube's recommendations and distractions, allowing you to focus solely on your practice.

## Purpose

The Yoga App was developed to solve a common problem - when you just want to do some morning yoga, YouTube's algorithm constantly tries to seduce you with other videos. This app creates a focused environment with carefully selected yoga videos for different needs and skill levels.

## Features

- **Distraction-Free Environment**: Watch yoga videos without YouTube's recommended videos and distractions
- **Curated Video Selection**: Hand-picked yoga videos for various purposes and levels
- **Simple Navigation**: Clean, intuitive interface focused on the yoga experience
- **Mobile-Optimized**: Designed specifically for Android devices
- **Responsive Design**: Works well on different screen sizes

## Video Library

The app currently includes the following curated videos:

- Yoga for Beginners
- 30 Min Full Body Yoga
- Morning Yoga Routine
- Yoga for Relaxation

## Technology Stack

- **Frontend**: SvelteKit
- **Mobile Platform**: Android (Capacitor/Cordova)
- **Styling**: Custom CSS with responsive design
- **Media**: YouTube iframe embedding

## Development

This application is built using SvelteKit and packaged for Android devices. The build process compiles the web application into a native Android app.

### Project Structure

- `/src` - Source code for the SvelteKit application
- `/android` - Android-specific configuration and assets
- `/build` - Build output for the web version
- `.svelte-kit` - SvelteKit generated files

### Building and Running

To run the development server:

```bash
npm run dev
```

To build the Android app:

```bash
npm run build
npx cap sync android
npx cap open android
```

## Installation

The app can be installed on Android devices via the APK file or through the Google Play Store (if published).

## Future Enhancements

- Add more curated yoga videos
- Implement video categories (beginner, intermediate, advanced)
- Add offline mode support
- Include favorites or bookmarking feature
- Add timer/scheduling functionality

## License

This is just a fancy youtube wrapper, no license needed.

## Credits

Created by David Strasak
