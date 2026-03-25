import { useState } from "react";

export default function Home() {
  const [coins, setCoins] = useState(1000);
  const [result, setResult] = useState("🎰");

  const spin = () => {
    const symbols = ["🍒","🍋","💎","⭐","7️⃣"];
    const r1 = symbols[Math.floor(Math.random()*symbols.length)];
    const r2 = symbols[Math.floor(Math.random()*symbols.length)];
    const r3 = symbols[Math.floor(Math.random()*symbols.length)];

    setResult(r1 + " " + r2 + " " + r3);

    if (r1 === r2 && r2 === r3) {
      setCoins(c => c + 300);
    } else {
      setCoins(c => c - 50);
    }
  };

  return (
    <div style={{
      background: "black",
      color: "white",
      height: "100vh",
      display: "flex",
      flexDirection: "column",
      alignItems: "center",
      justifyContent: "center"
    }}>
      <h1 style={{color: "gold"}}>🎰 PlayCasino</h1>
      <h2>{result}</h2>
      <p>🪙 {coins} coins</p>
      <button onClick={spin} style={{
        padding: "15px 30px",
        fontSize: "20px",
        marginTop: "20px"
      }}>
        SPIN
      </button>
      <p style={{marginTop: "20px", opacity: 0.6}}>
        No real money - just fun
      </p>
    </div>
  );
}
