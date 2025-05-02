Price

<span>
  {property.price.toLocaleString('en-US', {
    style: 'currency',
    currency: 'USD',
  })}
  </span>

  M2 to sqft
                  <span>
                {property.area && typeof property.area === "number"
                ? (property.area * 10.764).toFixed(2)
                : ""} sqft </span>



const valorComVirgulas = "1,234,567";
const valorNumerico = Number(valorComVirgulas.replace(/,/g, ""));
console.log(valorNumerico + 1000); // 1235567