## Countdown

**Installation**
```
npm install react-countdown
```

**App.jsx**
```
import { useRef } from 'react';
import Countdown from 'react-countdown';

function App() {
    const targetDate = new Date("2025-11-23T00:00:00");
    const renderer = ({ months, days, hours, minutes, seconds, completed }) => {
        if (completed) {
            return <span>Complete</span>;
        } else {
            const months = Math.floor(days / 30);
            const remainingDays = days % 30;
            
            return (
                <span>
                    {months} months &nbsp;
                    {remainingDays} days &nbsp;
                    {hours} hours &nbsp;
                    {minutes} minutes &nbsp;
                    {seconds} seconds
                </span>
            );
        }
    };

    return (
        <div className="App">
            <Countdown date={targetDate} renderer={renderer} />
        </div>
    );
}    
```

