import React, { useState } from 'react';

function ClickCounter() {
  const [count, setCount] = useState(0);
  const [message, setMessage] = useState('');

  const increaseCount = () => {
    const newCount = count + 1;
    setCount(newCount);
    checkThreshold(newCount);
  };

  const decreaseCount = () => {
    if (count > 0) {
      const newCount = count - 1;
      setCount(newCount);
      checkThreshold(newCount);
    }
  };

  const checkThreshold = (value) => {
    if (value >= 10) {
      setMessage("You've reached the limit!");
    } else {
      setMessage('');
    }
  };

  return (
    <div style={styles.container}>
      <h1 style={styles.title}>Click Counter</h1>
      <p style={styles.counter}>Count: {count}</p>
      {message && <p style={styles.message}>{message}</p>}
      <div style={styles.buttonContainer}>
        <button 
          onClick={increaseCount} 
          style={styles.button}
        >
          Increase
        </button>
        <button 
          onClick={decreaseCount} 
          style={{...styles.button, ...(count === 0 && styles.disabledButton)}}
          disabled={count === 0}
        >
          Decrease
        </button>
      </div>
    </div>
  );
}

const styles = {
  container: {
    display: 'flex',
    flexDirection: 'column',
    alignItems: 'center',
    justifyContent: 'center',
    minHeight: '100vh',
    fontFamily: 'Arial, sans-serif',
    backgroundColor: '#f5f5f5',
    padding: '20px',
  },
  title: {
    fontSize: '2rem',
    color: '#333',
    marginBottom: '20px',
  },
  counter: {
    fontSize: '1.5rem',
    margin: '20px 0',
  },
  message: {
    color: 'red',
    fontWeight: 'bold',
    margin: '10px 0',
  },
  buttonContainer: {
    display: 'flex',
    gap: '10px',
  },
  button: {
    padding: '10px 20px',
    fontSize: '1rem',
    backgroundColor: '#4CAF50',
    color: 'white',
    border: 'none',
    borderRadius: '4px',
    cursor: 'pointer',
    transition: 'background-color 0.3s',
  },
  disabledButton: {
    backgroundColor: '#cccccc',
    cursor: 'not-allowed',
  },
};

export default ClickCounter;
