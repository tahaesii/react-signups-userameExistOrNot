# Signup Component with Debounced Username Validation

This repository contains a React implementation of a sign-up form that features debounced username validation. The form ensures that usernames are checked against a predefined list to verify availability, providing a seamless and responsive user experience.

## Features

- **Debounced Input Handling**: Reduces the frequency of validation checks by using a debounce hook to wait for user input to stabilize.
- **Dynamic Validation Feedback**: Displays validation feedback to indicate whether the username is available.
- **Loading Indicator**: Shows a spinner while the input is being validated.
- **Disabled Button**: Prevents form submission until a valid username is entered.

## Code Overview

### Components

1. **`useDebounce` Hook**
   A custom hook that delays updates to the debounced value until the user stops typing for a specified delay period.

   ```typescript
   const useDebounce = (value: string, delay: number) => {
     const [debouncedValue, setDebouncedValue] = useState<string>(value);

     useEffect(() => {
       const handler = setTimeout(() => {
         setDebouncedValue(value);
       }, delay);
       return () => {
         clearTimeout(handler);
       };
     }, [value, delay]);

     return debouncedValue;
   };
   ```

2. **`Username` Component**
   Handles the username input field and displays validation feedback, including a loading spinner.

   ```typescript
   type UsernameProps = {
     isValid: boolean;
     isLoading: boolean;
     handleChange: (e: ChangeEvent<HTMLInputElement>) => void;
   };
   ```

3. **`Signup` Component**
   Implements the main form logic, integrating the `Username` component and the `useDebounce` hook for validation.

### Styles

Basic styles for the input fields, spinner, and validation feedback are included in `styles.css`. Adjust as necessary for your application.

### Validation Logic

The validation checks against a predefined list of usernames:

```typescript
const usernames = ["donald", "david", "patrik"];
```

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

4. Open your browser and navigate to `http://localhost:3000`.


## Future Enhancements

- **Backend Integration**: Replace the hardcoded username list with an API call to check username availability.
- **Form Validation**: Extend validation to other fields like password strength.


