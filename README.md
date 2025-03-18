# DemoApp - Application de Démo React Native avec TypeScript

Ce projet est une démonstration d'une application mobile créée avec **React Native** et **TypeScript**. L'application montre comment configurer une application de base, ajouter de la navigation entre différents écrans, intégrer des animations et personnaliser l'interface utilisateur.

## Prérequis

Avant de commencer, assurez-toi d'avoir installé les outils suivants :

- **Node.js** (version 14 ou plus) - [Télécharger Node.js](https://nodejs.org/)
- **npm** (ou **yarn**) - npm est installé automatiquement avec Node.js
- **Expo CLI** - Un outil pour créer et tester des applications React Native
  ```bash
  npm install -g expo-cli
  ```
- **Expo Go** - Une application mobile pour tester des projets Expo (disponible sur [Google Play](https://play.google.com/store/apps/details?id=host.exp.exponent) ou [App Store](https://apps.apple.com/us/app/expo-go/id982107779))

## Installation du projet

### 1. Créer le projet avec Expo et TypeScript

Lance la commande suivante pour créer un projet Expo avec TypeScript :

```bash
expo init DemoApp
```

Choisi l'option **blank (TypeScript)** pour obtenir un projet de base avec TypeScript.

### 2. Installer les dépendances nécessaires

Une fois le projet créé, installe les dépendances suivantes pour ajouter la navigation et les animations à ton projet :

```bash
npm install @react-navigation/native
npm install @react-navigation/stack
npm install react-native-screens react-native-safe-area-context
npm install react-native-gesture-handler react-native-reanimated
npm install react-native-animatable
```

### 3. Démarrer le projet

Pour démarrer l'application, exécute la commande suivante :

```bash
expo start |ou| npx expo start
```

Cela lancera le serveur Expo et ouvrira une page dans votre navigateur avec un QR code. Scanne ce code avec l'application **Expo Go** sur ton téléphone pour voir l'application en direct.

## Structure du projet

Le projet est structuré comme suit :

```
DemoApp/
│
├── App.tsx                  # Point d'entrée de l'application
├── package.json             # Gestion des dépendances et des scripts
├── screens/                 # Dossier contenant les écrans de l'application
│   ├── HomeScreen.tsx       # Écran principal de l'application
│   └── AboutScreen.tsx      # Écran d'informations sur l'application
└── node_modules/            # Dépendances installées
```

## Fonctionnalités principales

### 1. **Navigation entre les écrans**

L'application utilise **React Navigation** pour permettre la navigation entre deux écrans : **HomeScreen** et **AboutScreen**.

#### Code de la navigation dans `App.tsx` :

```tsx
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import HomeScreen from './screens/HomeScreen';
import AboutScreen from './screens/AboutScreen';

const Stack = createStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Home">
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="About" component={AboutScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

### 2. **HomeScreen**

L'écran d'accueil permet de changer le texte affiché en appuyant sur un bouton et de naviguer vers l'écran "About".

#### Code de `HomeScreen.tsx` :

```tsx
import React, { useState } from 'react';
import { StyleSheet, Text, View, Button } from 'react-native';

export default function HomeScreen({ navigation }: any) {
  const [message, setMessage] = useState<string>("Bienvenue dans React Native avec TypeScript!");

  const changeMessage = () => {
    setMessage("Le message a changé!");
  };

  return (
    <View style={styles.container}>
      <Text style={styles.text}>{message}</Text>
      <Button title="Changer le message" onPress={changeMessage} />
      <Button title="Voir plus" onPress={() => navigation.navigate('About')} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#fff',
  },
  text: {
    fontSize: 20,
    marginBottom: 20,
  },
});
```

### 3. **AboutScreen**

L'écran "About" présente un message d'information sur l'application.

#### Code de `AboutScreen.tsx` :

```tsx
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function AboutScreen() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Ceci est un écran d'information sur l'application</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f0f0f0',
  },
  text: {
    fontSize: 20,
  },
});
```

### 4. **Animations**

J'ai ajouté des animations avec **React Native Animatable** pour rendre l'application plus dynamique.

#### Exemple d'animation dans `HomeScreen.tsx` :

```tsx
import * as Animatable from 'react-native-animatable';

<Animatable.Text
  style={styles.text}
  animation="fadeIn"
  iterationCount={1}
  direction="alternate"
>
  {message}
</Animatable.Text>
```

Cela fait apparaître le texte avec une animation de fondu.

## Personnalisation de l'interface

Le projet utilise des styles de base en **React Native** avec `StyleSheet` pour organiser le visuel des écrans.

### Exemple de style dans `HomeScreen.tsx` :

```tsx
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#fff',
  },
  text: {
    fontSize: 20,
    marginBottom: 20,
  },
});
```

Tu peux personnaliser les couleurs, les tailles de texte et bien d'autres éléments selon tes besoins.

## Tester l'application

Pour tester l'application sur un émulateur Android ou iOS, tu peux appuyer sur les touches suivantes dans le terminal :

- **"a"** pour ouvrir l'émulateur Android
- **"i"** pour ouvrir l'émulateur iOS

## Conclusion

Ce projet te montre comment utiliser **React Native** avec **TypeScript** pour créer une application mobile de base avec navigation, animations et une interface utilisateur personnalisée. C'est une excellente introduction à React Native, et tu peux l'étendre en ajoutant des fonctionnalités comme la gestion d'état, des appels API ou une base de données pour rendre l'application plus interactive et fonctionnelle.

---

### Liens utiles

- [Documentation React Native](https://reactnative.dev/)
- [Documentation React Navigation](https://reactnavigation.org/)
- [Documentation React Native Animatable](https://github.com/oblador/react-native-animatable)
```
