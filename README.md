# rn-assignment5-11356558
Overview
The SettingsScreen component is a React Native component that provides a settings interface for users. It allows users to toggle between dark and light themes and navigate to different settings options like "Language", "My Profile", "Contact Us", "Change Password", and "Privacy Policy". The component also includes a footer for easy navigation between main screens.

Table of Contents
Installation
Usage
Components
Styles
Props
Context
Installation
Ensure you have react-native, react-navigation, and react-native-elements installed in your project.
Copy the SettingsScreen component into your project directory.
Import the SettingsScreen component where needed.
Usage
Import and use the SettingsScreen component in your navigation structure:

javascript
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import SettingsScreen from './path-to-SettingsScreen';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Settings">
        <Stack.Screen name="Settings" component={SettingsScreen} />
        {/* Other screens */}
      </Stack.Navigator>
    </NavigationContainer>
  );
};

export default App;
Components
Footer
The Footer component is used for navigation and includes icons for "Home", "My Card", "Stats", and "Settings".

SettingsScreen
The main settings interface that allows users to navigate to different settings options and toggle the theme.

Styles
The component uses StyleSheet for styling. There are different styles for dark and light themes.

Main Styles
container: Main container with default background color and margin.
contentContainer: Container for settings content with padding.
title: Style for the title text.
setting: Style for individual setting items.
settingText: Style for setting item text.
footer: Style for the footer container.
iconContainer: Style for each icon in the footer.
iconLabel: Style for the label under each icon.
Dark Mode Styles
darkContainer: Dark mode background for the main container.
darkContentContainer: Dark mode background for the content container.
darkText: Dark mode text color.
darkFooter: Dark mode background for the footer.
Props
Footer Props
navigation: React Navigation prop for navigating between screens.
isDarkTheme: Boolean to indicate if dark mode is enabled.
SettingsScreen Props
navigation: React Navigation prop for navigating between screens.
Context
ThemeContext
The component uses ThemeContext to manage theme state. The context provides:

isDarkTheme: Boolean indicating if dark mode is active.
toggleTheme: Function to toggle between dark and light themes.
To use the ThemeContext, ensure you have it defined and provided in your app:

javascript
import React, { useState } from 'react';

export const ThemeContext = React.createContext();

const ThemeProvider = ({ children }) => {
  const [isDarkTheme, setIsDarkTheme] = useState(false);

  const toggleTheme = () => {
    setIsDarkTheme(!isDarkTheme);
  };

  return (
    <ThemeContext.Provider value={{ isDarkTheme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

export default ThemeProvider;
Wrap your app with the ThemeProvider to provide the theme context:

javascript
Copy code
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import SettingsScreen from './path-to-SettingsScreen';
import ThemeProvider from './path-to-ThemeProvider';

const Stack = createStackNavigator();

const App = () => {
  return (
    <ThemeProvider>
      <NavigationContainer>
        <Stack.Navigator initialRouteName="Settings">
          <Stack.Screen name="Settings" component={SettingsScreen} />
          {/* Other screens */}
        </Stack.Navigator>
      </NavigationContainer>
    </ThemeProvider>
  );
};

export default App;





