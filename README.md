# React-Native-Example-Class

## Installing Watchman and initialize project with Expo

### Expo CLI
Expo CLI is a command-line tool that is the primary interface between a developer and other Expo tools. It is used for different tasks in the development life cycle of your project, such as serving the project in development, viewing logs, opening the app on an emulator or a physical device, and so on.

To use Expo CLI, you need to have the following tools installed on your developer machine:

Node.js LTS release
Git
Watchman for macOS or Linux users.

### Installing Watchman

```bash
sudo apt-get -y install watchman
```


```bash
sudo apt-get -f install
```


```bash
sudo apt-get -y install watchman
```
### Create a Project with Expo

The process of running a new Expo project consists of three steps.



1.- Initializing a Project

```bash
npx create-expo-app my-app && cd my-app
```


2.- Starting the development server with Expo CLI

```bash
npx expo strat
```

This process may take few minutes, but when the process finish we should see the following output: 

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/7b14175c-a40a-4f9f-af75-a9475be97e74)

Now we open Expo Go in our device and scan the QR code.
Remember to connect your device and computer to the same Wifi.



3-. Opening the app on your device with Expo Go to see your changes live

For Expo Go to work, we require:

To create an account in Expo’s website.
The computer and the mobile phone need to be connected to the same WiFi network.
We need download Expo Go in the App Store.We need download Expo Go in the App Store.

## First Steps

First when we start the project and open the Code Editor we shuould see the following project structure:

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/6e50237a-15e3-473d-a710-0fbc08fd1819)

Now we create a `components` folder and we create a `Header.js` and `Body.js` scripts.

```
import { useState } from "react";
import { ImageBackground } from "react-native";
import { SafeAreaView, StyleSheet, Text, View, Button, Alert, TextInput } from "react-native";

export default function Header() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>PokéApp</Text>
    </View>

  );
}

const styles = StyleSheet.create({
    container: {
        flex: 0.4,
    },
  text: {
    fontSize: 50,
    color: 'blue'
  },
});

```

```
import { useState } from "react";
import {
  SafeAreaView,
  StyleSheet,
  Text,
  View,
  Button,
  Alert,
  TextInput,
} from "react-native";

// The View component is the primary component for building UIs. It acts as a wrapper in which we will include every application component.
// Think of Views as a <div> element in HTML with a few differences.

export default function Body() {
  const [text, setText] = useState("");
  return (
    <View style={styles.container}>
        <View style={styles.text}>
            <Text>Hello: {text}</Text>
        </View>
      <View style={styles.inputContainer}>
        <TextInput style={styles.input} onChangeText={setText} value={text} placeholder="Your name here!!!" />
      </View>
      <View style={styles.button}>
        <Button title="Press me" onPress={() => Alert.alert(`Hello: ${text}`)} />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 0.2,
    alignItems: 'center',
    width: '90%'
  },
  input: {
    borderWidth: 1,
    margin: 10,
  },
  inputContainer: {
    width: '75%'

  },
  text: {
    alignContent: 'center'
  },button: {
    width: '30%'
  }
});
```


