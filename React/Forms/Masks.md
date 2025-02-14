Money
import { useState } from "react";

const CurrencyInput = () => {
  const [value, setValue] = useState("");

  const formatCurrency = (inputValue) => {
    // Remove tudo que não for número
    let numericValue = inputValue.replace(/\D/g, "");

    // Formata para exibir vírgulas corretamente
    return numericValue.replace(/\B(?=(\d{3})+(?!\d))/g, ",");
  };

  const handleChange = (event) => {
    const rawValue = event.target.value;
    const formattedValue = formatCurrency(rawValue);
    setValue(formattedValue);
  };

  return (
    <input
      type="text"
      value={value}
      onChange={handleChange}
      placeholder="Digite um valor"
    />
  );
};

export default CurrencyInput;