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

### Tab Navigator

Possibly the most common style of navigation in mobile apps is tab-based navigation. It is usually placed at the bottom of the screen.

Tab Navigator is not part of the core of React Navigator, so we need to install it to be able to use it.

```
npm install @react-navigation/bottom-tabs
```

Its API is very similar to the Navigation Stack. Our Navigation component would look similar to the following:

Now we reestructure the `App.js` and should see like this: 

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/dbd8581c-8735-4de9-8b6c-82b88b8887c4)

The next step is create a `PokedexScreen.js` , import in pur `App.js` and add a new `<Tab.Screen name='Pokedex' component={PokedexScreen} />`. In our `PokedexScreen.js` only create a Text component, then we will change the entire structure of the component. We should see a view like this in our `App.js`:


![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/8c0f4e41-82f6-4b83-a38c-07e6c1ea4b93)


In the image where  `<Tab.Screen name='Pokedex' component={PokedexScreenFake} />` is our `<Tab.Screen name='Pokedex' component={PokedexScreen} />`.

## Installing React Query

React Query is a library created for managing server state: it handles requests and queries to external services while optimizing performance. It requires zero-config but can be customized to your liking as your application grows.

```
npm i react-query
```

When the installation finihed we need to add this in our `App.js`:

```
import {
  QueryClient,
  QueryClientProvider,
} from 'react-query'

// Create a client
const queryClient = new QueryClient()
```
And add our QueryClientProvider in our aplication, you should see something like this:

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/81ebc666-68d4-4327-a42f-083544d16567)


### useQuery
To subscribe to a query in our components or custom hooks, we can call the useQuery hook.

useQuery requieres to work at least:
- A unique key (name) for the query
- A function that returns a promise that either resolves the data, or throws an error.

Create a `apiService.js` like in React:

```
import axios from "axios";

const api = axios.create({
  baseURL: `https://pokeapi.co/api/v2`,
});

export default api;
```

Then create the service you want, in this case i use PokeApi and the service show like this: 

```
import api from "./apiService";
export const getPokemons = async () => {
  try {
    const { data } = await api.get("/pokemon/?limit=151");
    return data;
  } catch (err) {
    throw new Error(err);
  }
};
```

Now we come back to PokdexScreen and import our Service and useQuery: 

```
import { useQuery } from "react-query";
import { getPokemons } from "../services/pokemonService";
```
Then inside of our component `PokedexScreen.js` we use useQuery:

```
export function PokedexScreen({ navigation }) {
  const { isLoading, isError, data, error } = useQuery("pokemons", getPokemons);
  if (isLoading) {
    return <Text>Loading...</Text>;
  }
  if (isError) {
    return <Text>Error: {error.message}</Text>;
  }

}
```
The next Step is to show the data in our `PokedexScreen.js` with a FlatList Component.

FlatList example:

```
const DATA = [
  {
    id: 'bd7acbea-c1b1-46c2-aed5-3ad53abb28ba',
    title: 'First Item',
  },
  {
    id: '3ac68afc-c605-48d3-a4f8-fbd91aa97f63',
    title: 'Second Item',
  },
  {
    id: '58694a0f-3da1-471f-bd96-145571e29d72',
    title: 'Third Item',
  },
];

const Item = (title) => (
  <View style={styles.item}>
    <Text style={styles.title}>{title}</Text>
  </View>
);

const App = () => {
  return (
    <SafeAreaView style={styles.container}>
      <FlatList
        data={DATA}
        renderItem={({item}) => <Item title={item.title} />}
        keyExtractor={item => item.id}
      />
    </SafeAreaView>
  );
};
```
In our `PokedexScreen.js` we aplly the above example and we should see something like this::

![image](https://github.com/Suareguen/React-Native-Example-Class/assets/103899316/c0b51adc-5e4b-422e-ac4c-0462474f8f62)


We have a Pokedex List created, now let's create a `PokemonScreen.js` to show some information about the pokemon we want.
In this Screen we receive some props passed trhough Item component in the `PokedexScreen.js`, in this case we pass in the navigation Button the name of our pokemon, an information obtained to show our Pokedex.

```
  const Item = ({ name, url }) => (
    <View style={{ alignItems: "center", borderWidth: 1, margin: 5, padding: 5, backgroundColor: 'grey', borderRadius: 4 }}>
      <Text>{capitalizeFirstLetter(name)}</Text>
      <View>
        <Button
          title="See More Details"
          onPress={() =>
            // Here we passs name as prop to the link Screen
            navigation.navigate("Pokemon", {
              //url: url,
              name: name,
            })
          }
        />
      </View>
    </View>
  );
```

In our Pokemon service created before, we add a new service to search an individual pokemon:

```
export const getPokemonsById = async (name) => {
  try {
    const { data } = await api.get(`/pokemon/${name}/`);
    return data;
  } catch (err) {
    throw new Error(err);
  }
};
```

Like in the `PokedexScreen.js` import the necessary apply the useQuery, you should see something like this:
TIP: You can make the component as you wish, this is only a guide.

```
import { Button, Image } from "react-native";
import { View, Text } from "react-native";
import { useQuery } from "react-query";
import { getPokemonsById } from "../services/pokemonService";

function capitalizeFirstLetter(string) {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

export function PokemonScreen({ route }) {
  const { name } = route.params;

  const { isLoading, isError, data, error } = useQuery("pokemon", (id) =>
    getPokemonsById(name)
  );
  if (isLoading) {
    return <Text>Loading...</Text>;
  }
  if (isError) {
    return <Text>Error: {error.message}</Text>;
  }
  const showTypes = (array) => {

      return array.map((type, idx) => {
        return <Text key={idx}>{type.type.name}</Text>;
  })}

  return (
    <>
      <View
        style={{
          flex: 1,
          alignItems: "center",
          justifyContent: "space-around",
          borderWidth: 3,
          margin: 5,
          padding: 5,
          backgroundColor: "grey",
          borderRadius: 4,
        }}
      >
        <View style={{ borderWidth: 2 }}>
          <Text>{capitalizeFirstLetter(name)}</Text>
          <View>
            <Image
              source={{ uri: data.sprites.front_default }}
              style={{ width: 200, height: 200 }}
            />
          </View>
        </View>
        <View style={{ borderWidth: 1 }}>
          <Text>Types: </Text>
          {showTypes(data.types)}
        </View>
      </View>
    </>
  );
}
```


















