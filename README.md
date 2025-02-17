import React, { useEffect, useState } from 'react';

// Function to get the current time in a specific time zone
const getTimeInTimeZone = (timeZone: string) => {
  return new Date().toLocaleTimeString('en-US', { timeZone });
};

const DigitalClock: React.FC = () => {
  // State to hold the current time for each time zone
  const [time, setTime] = useState({
    utc: getTimeInTimeZone('UTC'),
    est: getTimeInTimeZone('America/New_York'),
    pst: getTimeInTimeZone('America/Los_Angeles'),
    ist: getTimeInTimeZone('Asia/Kolkata'),
    jst: getTimeInTimeZone('Asia/Tokyo'),
  });

  // Update the time every second
  useEffect(() => {
    const intervalId = setInterval(() => {
      setTime({
        utc: getTimeInTimeZone('UTC'),
        est: getTimeInTimeZone('America/New_York'),
        pst: getTimeInTimeZone('America/Los_Angeles'),
        ist: getTimeInTimeZone('Asia/Kolkata'),
        jst: getTimeInTimeZone('Asia/Tokyo'),
      });
    }, 1000);

    return () => clearInterval(intervalId);
  }, []);

  return (
    <div style={{ textAlign: 'center', fontFamily: 'Arial, sans-serif' }}>
      <h1>Digital Clock</h1>
      <div>
        <h2>UTC</h2>
        <p>{time.utc}</p>
      </div>
      <div>
        <h2>EST</h2>
        <p>{time.est}</p>
      </div>
      <div>
        <h2>PST</h2>
        <p>{time.pst}</p>
      </div>
      <div>
        <h2>IST</h2>
        <p>{time.ist}</p>
      </div>
      <div>
        <h2>JST</h2>
        <p>{time.jst}</p>
      </div>
    </div>
  );
};

export default DigitalClock;
