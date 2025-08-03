# Vereinsheld
Für mein projekt

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/App.js
index 0000000000000000000000000000000000000000..77c88981a7c4b57041d77722d5b2e1e5987b24ef 100644
--- a//dev/null
+++ b/App.js
@@ -0,0 +1,40 @@
+import * as React from 'react';
+import { NavigationContainer } from '@react-navigation/native';
+import { createStackNavigator } from '@react-navigation/stack';
+
+import HomeScreen from './src/screens/HomeScreen';
+import EventsScreen from './src/screens/EventsScreen';
+import MembersScreen from './src/screens/MembersScreen';
+import PaymentsScreen from './src/screens/PaymentsScreen';
+
+// Create a stack navigator for simple navigation between screens.
+const Stack = createStackNavigator();
+
+export default function App() {
+  return (
+    <NavigationContainer>
+      <Stack.Navigator initialRouteName="Home">
+        <Stack.Screen
+          name="Home"
+          component={HomeScreen}
+          options={{ headerTitle: 'Vereinsheld' }}
+        />
+        <Stack.Screen
+          name="Events"
+          component={EventsScreen}
+          options={{ headerTitle: 'Veranstaltungen' }}
+        />
+        <Stack.Screen
+          name="Members"
+          component={MembersScreen}
+          options={{ headerTitle: 'Mitglieder' }}
+        />
+        <Stack.Screen
+          name="Payments"
+          component={PaymentsScreen}
+          options={{ headerTitle: 'Zahlungen' }}
+        />
+      </Stack.Navigator>
+    </NavigationContainer>
+  );
+}
 
EOF
)


 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/package.json
index 0000000000000000000000000000000000000000..b6bb1b3a579973dcb3cd596f86f1d1dba8ddcf49 100644
--- a//dev/null
+++ b/package.json
@@ -0,0 +1,21 @@
+{
+  "name": "vereinsheld_app",
+  "version": "0.0.1",
+  "private": true,
+  "scripts": {
+    "start": "react-native start",
+    "android": "react-native run-android",
+    "ios": "react-native run-ios"
+  },
+  "dependencies": {
+    "react": "18.2.0",
+    "react-native": "0.73.0",
+    "@react-navigation/native": "^6.1.7",
+    "@react-navigation/stack": "^6.3.18",
+    "react-native-safe-area-context": "^4.7.1",
+    "react-native-screens": "^3.25.0"
+  },
+  "devDependencies": {
+    "@babel/core": "^7.22.9"
+  }
+}
 
EOF
)

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/package.json
index 0000000000000000000000000000000000000000..b6bb1b3a579973dcb3cd596f86f1d1dba8ddcf49 100644
--- a//dev/null
+++ b/package.json
@@ -0,0 +1,21 @@
+{
+  "name": "vereinsheld_app",
+  "version": "0.0.1",
+  "private": true,
+  "scripts": {
+    "start": "react-native start",
+    "android": "react-native run-android",
+    "ios": "react-native run-ios"
+  },
+  "dependencies": {
+    "react": "18.2.0",
+    "react-native": "0.73.0",
+    "@react-navigation/native": "^6.1.7",
+    "@react-navigation/stack": "^6.3.18",
+    "react-native-safe-area-context": "^4.7.1",
+    "react-native-screens": "^3.25.0"
+  },
+  "devDependencies": {
+    "@babel/core": "^7.22.9"
+  }
+}
 
EOF
)

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/src/screens/EventsScreen.js
index 0000000000000000000000000000000000000000..9247d013c8fa48a09febd230713166344053ff3f 100644
--- a//dev/null
+++ b/src/screens/EventsScreen.js
@@ -0,0 +1,57 @@
+import React from 'react';
+import { View, Text, StyleSheet, FlatList, Button } from 'react-native';
+
+/**
+ * EventsScreen listet bevorstehende Vereinsveranstaltungen auf.
+ * In einer späteren Ausbaustufe könnten hier Eventdaten aus der Datenbank
+ * geladen und Details angezeigt werden. Aktuell dienen Platzhalter als Beispiele.
+ */
+const sampleEvents = [
+  { id: '1', title: 'Trainingslager', date: '2025-08-15' },
+  { id: '2', title: 'Vereinsfest', date: '2025-09-10' },
+  { id: '3', title: 'Mitgliederversammlung', date: '2025-10-05' },
+];
+
+export default function EventsScreen() {
+  return (
+    <View style={styles.container}>
+      <FlatList
+        data={sampleEvents}
+        keyExtractor={(item) => item.id}
+        renderItem={({ item }) => (
+          <View style={styles.eventItem}>
+            <Text style={styles.eventTitle}>{item.title}</Text>
+            <Text style={styles.eventDate}>{item.date}</Text>
+          </View>
+        )}
+      />
+      <View style={styles.buttonContainer}>
+        <Button title="Neues Event erstellen" onPress={() => { /* später implementieren */ }} />
+      </View>
+    </View>
+  );
+}
+
+const styles = StyleSheet.create({
+  container: {
+    flex: 1,
+    padding: 16,
+    backgroundColor: '#fff',
+  },
+  eventItem: {
+    padding: 12,
+    borderBottomWidth: 1,
+    borderBottomColor: '#ccc',
+  },
+  eventTitle: {
+    fontSize: 18,
+    fontWeight: '500',
+  },
+  eventDate: {
+    fontSize: 14,
+    color: '#666',
+  },
+  buttonContainer: {
+    marginTop: 16,
+  },
+});
 
EOF
)

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/src/screens/HomeScreen.js
index 0000000000000000000000000000000000000000..300f40bc7348e68862ca316a7fcd159038590227 100644
--- a//dev/null
+++ b/src/screens/HomeScreen.js
@@ -0,0 +1,49 @@
+import React from 'react';
+import { View, Text, StyleSheet, Button, Image } from 'react-native';
+
+/**
+ * HomeScreen dient als Startpunkt der App und bietet Verknüpfungen
+ * zu den wichtigsten Modulen. Das Logo wird oben angezeigt.
+ */
+export default function HomeScreen({ navigation }) {
+  return (
+    <View style={styles.container}>
+      <Image source={require('../../assets/logo.png')} style={styles.logo} />
+      <Text style={styles.title}>Willkommen bei Vereinsheld</Text>
+      <View style={styles.buttonContainer}>
+        <Button title="Veranstaltungen" onPress={() => navigation.navigate('Events')} />
+      </View>
+      <View style={styles.buttonContainer}>
+        <Button title="Mitglieder" onPress={() => navigation.navigate('Members')} />
+      </View>
+      <View style={styles.buttonContainer}>
+        <Button title="Zahlungen" onPress={() => navigation.navigate('Payments')} />
+      </View>
+    </View>
+  );
+}
+
+const styles = StyleSheet.create({
+  container: {
+    flex: 1,
+    justifyContent: 'center',
+    alignItems: 'center',
+    paddingHorizontal: 16,
+    backgroundColor: '#f5f5f5',
+  },
+  logo: {
+    width: 120,
+    height: 120,
+    marginBottom: 24,
+    resizeMode: 'contain',
+  },
+  title: {
+    fontSize: 22,
+    fontWeight: 'bold',
+    marginBottom: 32,
+  },
+  buttonContainer: {
+    width: '100%',
+    marginVertical: 8,
+  },
+});
 
EOF
)

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/src/screens/MembersScreen.js
index 0000000000000000000000000000000000000000..fdfcc5606aa02251a31462858ae0abebd5018bdb 100644
--- a//dev/null
+++ b/src/screens/MembersScreen.js
@@ -0,0 +1,56 @@
+import React from 'react';
+import { View, Text, StyleSheet, FlatList, Button } from 'react-native';
+
+/**
+ * MembersScreen zeigt eine Liste von Vereinsmitgliedern an.
+ * Später können hier Filter, Suchfunktionen und Detailansichten ergänzt werden.
+ */
+const sampleMembers = [
+  { id: '1', name: 'Max Mustermann', status: 'aktiv' },
+  { id: '2', name: 'Erika Beispiel', status: 'aktiv' },
+  { id: '3', name: 'Hans Schüler', status: 'inaktiv' },
+];
+
+export default function MembersScreen() {
+  return (
+    <View style={styles.container}>
+      <FlatList
+        data={sampleMembers}
+        keyExtractor={(item) => item.id}
+        renderItem={({ item }) => (
+          <View style={styles.memberItem}>
+            <Text style={styles.memberName}>{item.name}</Text>
+            <Text style={styles.memberStatus}>Status: {item.status}</Text>
+          </View>
+        )}
+      />
+      <View style={styles.buttonContainer}>
+        <Button title="Mitglied hinzufügen" onPress={() => { /* später implementieren */ }} />
+      </View>
+    </View>
+  );
+}
+
+const styles = StyleSheet.create({
+  container: {
+    flex: 1,
+    padding: 16,
+    backgroundColor: '#fff',
+  },
+  memberItem: {
+    padding: 12,
+    borderBottomWidth: 1,
+    borderBottomColor: '#ccc',
+  },
+  memberName: {
+    fontSize: 18,
+    fontWeight: '500',
+  },
+  memberStatus: {
+    fontSize: 14,
+    color: '#666',
+  },
+  buttonContainer: {
+    marginTop: 16,
+  },
+});
 
EOF
)

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a//dev/null b/src/screens/PaymentsScreen.js
index 0000000000000000000000000000000000000000..697b7c33de3317fb1a67f9592f64d8d43460e0a7 100644
--- a//dev/null
+++ b/src/screens/PaymentsScreen.js
@@ -0,0 +1,29 @@
+import React from 'react';
+import { View, Text, StyleSheet, Button } from 'react-native';
+
+/**
+ * PaymentsScreen wird Zahlungen des Vereins verwalten.
+ * Aktuell dient er als Platzhalter.
+ */
+export default function PaymentsScreen() {
+  return (
+    <View style={styles.container}>
+      <Text style={styles.title}>Zahlungen</Text>
+      <Button title="Zahlung hinzufügen" onPress={() => { /* später implementieren */ }} />
+    </View>
+  );
+}
+
+const styles = StyleSheet.create({
+  container: {
+    flex: 1,
+    justifyContent: 'center',
+    alignItems: 'center',
+    padding: 16,
+    backgroundColor: '#fff',
+  },
+  title: {
+    fontSize: 18,
+    marginBottom: 16,
+  },
+});
 
EOF
)
