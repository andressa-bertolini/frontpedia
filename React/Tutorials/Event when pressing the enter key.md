```
import React, { useState } from 'react';

const App = () => {
    const [inputValue, setInputValue] = useState('');

    // Função chamada ao pressionar Enter
    const handleKeyDown = (event) => {
        if (event.key === 'Enter') {
            console.log('Enter foi pressionado!');
            console.log('Valor do input:', inputValue);
            // Adicione sua lógica aqui
        }
    };

    return (
        <div>
            <h1>Pressione Enter</h1>
            <input
                type="text"
                value={inputValue}
                onChange={(e) => setInputValue(e.target.value)} // Atualiza o estado
                onKeyDown={handleKeyDown} // Captura a tecla pressionada
                placeholder="Digite algo e aperte Enter"
            />
        </div>
    );
};

export default App;
```