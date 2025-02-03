# Select

**components/CustomSelect.jsx**

```
import { useState, useRef, useEffect } from "react";

const CustomSelect = () => {
  const [isOpen, setIsOpen] = useState(false);
  const selectRef = useRef(null);

  const toggleSelect = () => {
    setIsOpen((prev) => !prev);
  };

  const handleClickOutside = (event) => {
    if (selectRef.current && !selectRef.current.contains(event.target)) {
      setIsOpen(false);
    }
  };

  useEffect(() => {
    document.addEventListener("mousedown", handleClickOutside);

    return () => {
      document.removeEventListener("mousedown", handleClickOutside);
    };
  }, []);

  return (
    <div ref={selectRef} className="custom-select">
      <button onClick={toggleSelect} className="select-button">
        Select Option
      </button>
      {isOpen && (
        <ul className="select-options">
          <li>Option 1</li>
          <li>Option 2</li>
          <li>Option 3</li>
        </ul>
      )}
    </div>
  );
};

export default CustomSelect;
```