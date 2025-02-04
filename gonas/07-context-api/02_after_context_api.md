# After Context API
After Context API, we do not need to pass props step by step from parents to childs. We can directly pass or declear props globally and recive directly from the childs. 

**1. ModalContext.js**
```js
import { createContext } from "react";

export const ModalContext = createContext();
```


**2. App.jsx**
```jsx
import { useState } from "react";
import { Modal } from "./components/Modal";
import { ModalContext } from "./contexts/ModalContext";

function App() {
  const [isModalOpen, setIsModalOpen] = useState(false);
  const openModal = () => setIsModalOpen(true);
  const closeModal = () => setIsModalOpen(false);

  return (
    <ModalContext.Provider value={{ closeModal }}>
      <button onClick={openModal}>Open Modal</button>
      {isModalOpen && <Modal />}
    </ModalContext.Provider>
  );
}

export default App;
```


**3. Modal.jsx**
```jsx
import { ModalCloseBtn } from "./ModalCloseBtn";

export const Modal = () => {
  return (
    <div style={{ border: "1px solid gray", padding: "1rem" }}>
      <div>
        <h1>Modal title</h1>
        <p>This is a modal content</p>
      </div>
      <ModalCloseBtn />
    </div>
  );
};
```


**4. ModalCloseBtn**
```jsx
import { useContext } from "react";
import { ModalContext } from "../contexts/ModalContext";

export const ModalCloseBtn = () => {
  const { closeModal } = useContext(ModalContext);
  return <button onClick={closeModal}>Close</button>;
};
```
