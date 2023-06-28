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
You should have a structure like this: 
![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/4b811a7a-4b92-4344-a3c9-b72c6be8363c)

Now in the Header we can create a Header Component where we show the Title of the App. (You can see the component in the folder components of this  repository.

The next step is to import the Header and Body components in the `App.js` like this:

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/171a17ff-79b2-4d2e-9d80-c6b11bf115f5)

And you should see a view like this in your device: 


![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/d65c3bbc-5090-464d-a775-6b3860b97fb7)



## Installing React Navigator

Installing React Navigation for React Native requires installing the required packages in our project:

```
npm install @react-navigation/native
```

To frontload the installation work, let’s also install and configure dependencies used by most navigators; then, we can start writing some code.

The libraries we will install now are react-native-screens and react-native-safe-area-context.

```
npx expo install react-native-screens react-native-safe-area-context

```

For our App to be able to render different screens, we need to set up all the various components and manage how to move between them. First we need to install the component that handles navigation.

```
npm install @react-navigation/native-stack
```
``` createNativeStackNavigator``` is a function that returns an object containing two properties: Screen and Navigator. Screen lets us configure the different screens in our app, while Navigator manages the routing between the screens.



The Navigator should contain Screen elements as its children to define the route configuration.
Create a folder named `screens` and add a `HomeScreen.js` component, then copy the structure typed in `App.js` and paste in the `HomeScree.js`. You should see something like this: 

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/5b634da3-736c-4970-a0cd-191014a1c513)


Let's create another Screen, `Details.js` for example, like this:

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/8d622ca6-edab-4623-aa31-2eef287633f5)


We need to import in our `App.js`:
```
import { NavigationContainer } from "@react-navigation/native";
import { createNativeStackNavigator } from "@react-navigation/native-stack";
```

Next Steps:
- NavigationContainer is a component that manages our navigation tree and contains the navigation state. 
This component must wrap up the navigator’s structure. 
- Creates a navigation component named Stack using the createNativeStackNavigator() function provided by the @react-navigation/native-stack library.
This Stack component is used to define and manage stack-based navigation in your React Native application.

In our `App.js` we should see someting like this:


![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/b0fd0ab7-2f3e-4192-b09b-f40cd579d402)


As we can see in the Button component we have a onPress property to launch our navigation property which contains a navigate method to specify the Screen we wants to go, a second paramater can be passed through the navigate method and this would be received in the component we go and we can use this value in the new component.

HomeScreen

```

            <Button
              title="Go to Details"
              //Como segundo parámetro podemos pasar props a las Screens que vayamos a enlazar, 
              // en este caso le pasamos un id con el valor de 'textProp'
              onPress={() =>
                navigation.navigate("Details", {
                  id: "textProp",
                })
              }
            />
}
```

***DetailsScreen***


```

export default function DetailsScreen({ navigation, route }) {

    // Podemos por medio del objeto route obtener el id que le hemos pasado desde la ScreenHome
    const { id } = route.params

  return (
    <>
      <SafeAreaView style={styles.container}>
        <Text>Details</Text>
        {/* En el Text veriamos el valor de textProp pasado anteriormente desde HomeScreen */}
        <Text>Text Prop: { id }</Text>

        <View>
          <Button
            title="Go to Home"
            onPress={() => navigation.navigate("Home")}
          />
        </View>
      </SafeAreaView>
    </>
  );
}
```

## Installing Navigation Menus

React Navigation offers different GUI elements which we can use to implement navigation for our users.

###Tab Navigator

Possibly the most common style of navigation in mobile apps is tab-based navigation. It is usually placed at the bottom of the screen.













