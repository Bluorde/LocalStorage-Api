# LocalStorage-Api
# JavaScript 30: Save Data to Local Storage & Persist Form States

This project is part of the [JavaScript 30](https://javascript30.com/) challenge by Wes Bos. It demonstrates how to save data to the browser's local storage and persist form states across sessions using vanilla JavaScript.

## Features

- **Local Storage Integration:** Save user input in the browser's local storage.
- **Form State Persistence:** Automatically restore form fields with previously entered data when the page is reloaded.
- **Real-time Updates:** Changes to form inputs are saved to local storage immediately as the user types.

## Technologies Used

- Vanilla JavaScript
- Local Storage API
- HTML & CSS

## How It Works

1. **Event Listeners:**  
   Add `input` or `change` event listeners to the form fields to detect changes in user input.
   
2. **Saving Data:**  
   Serialize form data as JSON and store it in the browser's local storage.

3. **Restoring Data:**  
   On page load, check local storage for saved data. If data is found, populate the form fields with it.

## Code Overview

### Saving Data to Local Storage

```javascript
const form = document.querySelector('form');
const inputs = form.querySelectorAll('input, textarea');

function saveToLocalStorage() {
  const formData = {};
  inputs.forEach(input => {
    formData[input.name] = input.value;
  });
  localStorage.setItem('formData', JSON.stringify(formData));
}

inputs.forEach(input => input.addEventListener('input', saveToLocalStorage));
```

### Restoring Form State

```javascript
function restoreFormState() {
  const savedData = JSON.parse(localStorage.getItem('formData'));
  if (savedData) {
    inputs.forEach(input => {
      if (savedData[input.name]) {
        input.value = savedData[input.name];
      }
    });
  }
}

window.addEventListener('DOMContentLoaded', restoreFormState);
```

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/js30-local-storage.git
   ```
2. Open the `index.html` file in your browser.

3. Fill out the form fields. Your input will save to local storage upon click of the +Add Item button.

4. Refresh the page. The form will reload with your previously entered data.

## Live Demo

Check out a live demo [here](#).

## License

This project is free to use under the [MIT License](LICENSE).

---
