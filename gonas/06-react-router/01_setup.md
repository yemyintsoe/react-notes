# Installation
```
npm install react-router
```

# Setup basic route
```js
import { BrowserRouter, Routes, Route, NavLink } from "react-router";
import { Home } from "./pages/Home";
import { About } from "./pages/About";
import { Contact } from "./pages/Contact";

function App() {
  return (
    <>
      <BrowserRouter>
        <nav className="container mx-auto mb-5 px-12 py-3">
          <ul className="flex gap-5">
            <li>
              <NavLink to="/">Home</NavLink>
            </li>
            <li>
              <NavLink to="/about">About</NavLink>
            </li>
            <li>
              <NavLink to="/contact">Contact</NavLink>
            </li>
          </ul>
        </nav>

        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="about" element={<About />} />
          <Route path="contact" element={<Contact />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}

export default App;
```

## Sidenote
<Link>, <NavLink> will not work outside of the <BrowserRouter>, so that it's required to be wrapped by BrowserRouter