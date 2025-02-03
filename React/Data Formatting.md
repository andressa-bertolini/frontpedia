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