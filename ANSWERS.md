# Checkpoint Questions

1. **What does the `visible` prop of `Modal` do and why do we control it with `useState`?**
   The `visible` prop controls whether the modal is displayed (`true`) or hidden (`false`) on the screen. Controlling it with `useState` lets React re-render the interface whenever the user opens or closes the dialog.

2. **What is `onRequestClose` for? What happens on Android if you do not close the modal in it?**
   `onRequestClose` is a callback triggered when the user presses the hardware or gesture *Back* button on Android (or the Menu button on Apple TV). If you do not update the state to close the modal inside `onRequestClose`, pressing the Android back button will not dismiss the modal and the user can get stuck.

3. **What is the effect of `transparent={true}`? Name the three values of `animationType`.**
   `transparent={true}` renders the modal over a transparent background so the underlying screen remains visible through a semi-transparent backdrop overlay instead of covering it with a solid white box. The three valid values for `animationType` are `'none'`, `'slide'`, and `'fade'`.

4. **Why does `ScrollView` exist? What happens with a long `View` without it? When would you choose `FlatList` instead?**
   `ScrollView` provides a scrollable container for content that exceeds the height or width of the screen. Without it, a long `View` simply clips or overflows off the screen and cannot be scrolled by the user. You should choose `FlatList` instead when rendering large or dynamic data sets because `FlatList` lazily renders only the items currently visible on screen, saving memory.

5. **What is the difference between the `style` and the `contentContainerStyle` props of a `ScrollView`?**
   `style` applies layout and appearance rules to the outer scroll viewport itself (such as `flex: 1`, `maxHeight`, or background color). `contentContainerStyle` applies styles to the inner wrapper that holds all child items, which is where you put `padding`, `gap`, or `justifyContent`.

6. **What is `SafeAreaView` for and which zones of the device does it protect? Why do we use `react-native-safe-area-context`?**
   `SafeAreaView` automatically adds padding so UI elements are not obscured by physical device features like the camera notch, Dynamic Island, status bar, or bottom home indicator. We use `react-native-safe-area-context` because React Native's built-in `SafeAreaView` only works on iOS, whereas `react-native-safe-area-context` works reliably across both iOS and Android.

7. **Write the three best practices from the Step 5 checklist in your own words and give an example of when a modal is *not* a good idea.**
   First, use modals sparingly and only for short, focused tasks rather than complex multi-step workflows. Second, keep the number of items inside a `ScrollView` small since it renders all children at once. Third, always wrap screens in `SafeAreaView` so content respects system bars and notches. A modal is **not** a good idea for displaying long forms, full articles, or multi-screen navigation flows that belong on a dedicated screen.