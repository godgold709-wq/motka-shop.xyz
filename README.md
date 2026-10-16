<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Notza Shop - ร้านค้าออนไลน์</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/lucide@latest"></script>
  <script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <style>
    @keyframes rainbow-bg {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    .rainbow-button {
      background: linear-gradient(90deg, #ff0000, #ff7f00, #ffff00, #00ff00, #0000ff, #4b0082, #8b00ff);
      background-size: 400% 400%;
      animation: rainbow-bg 5s ease infinite;
      color: white;
    }
  </style>
</head>
<body class="bg-slate-900 text-white min-h-screen">
  <div id="root"></div>
  <script type="text/babel">
    const { useState } = React;
    function App() {
      const [balance] = useState(500);
      const [products] = useState([
        { id: 1, name: "ขนาดสินค้าแนะนำ 380x380 1", price: 0, stock: 10, img: "https://via.placeholder.com/380x380?text=380x380", badge: "ยอดฮิต" },
        { id: 2, name: "แมว", price: 100, stock: 0, img: "https://via.placeholder.com/380x380/111/fff?text=Cat", badge: "" },
        { id: 3, name: "ขนาดสินค้าแนะนำ 380x380 3", price: 0, stock: 10, img: "https://via.placeholder.com/380x380?text=380x380", badge: "สินค้าขายดี" },
      ]);
      return (
        <div class="min-h-screen p-4 max-w-6xl mx-auto">
          <header class="flex justify-between items-center py-4 border-b border-slate-700 mb-6">
            <h1 class="text-2xl font-bold text-cyan-400">Notza.shop.xyz</h1>
            <div class="flex items-center gap-4">
              <span class="bg-slate-800 px-3 py-1 rounded-full text-yellow-400 font-semibold">💰 ฿{balance}</span>
              <button class="rainbow-button px-4 py-2 rounded-lg font-bold shadow-lg">เข้าสู่ระบบ / สมัครสมาชิก</button>
            </div>
          </header>
          <div class="mb-8">
            <h2 class="text-xl font-bold mb-4">⭐ หมวดหมู่แนะนำ</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div class="border-2 border-cyan-500/50 bg-gradient-to-r from-purple-900 to-indigo-900 h-36 rounded-2xl flex items-center justify-center font-bold text-2xl text-cyan-200 shadow-lg">หมวดหมู่ 960x300</div>
              <div class="border-2 border-purple-500/50 bg-gradient-to-r from-indigo-900 to-purple-900 h-36 rounded-2xl flex items-center justify-center font-bold text-2xl text-purple-200 shadow-lg">หมวดหมู่ 960x300</div>
            </div>
          </div>
          <div>
            <h2 class="text-xl font-bold mb-4">⭐ สินค้าแนะนำ</h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
              {products.map((p) => (
                <div key={p.id} class="bg-slate-800 rounded-xl p-3 border border-slate-700 relative flex flex-col justify-between">
                  {p.badge && <span class={`absolute top-5 right-5 text-xs font-bold px-2 py-1 rounded ${p.badge === 'ยอดฮิต' ? 'bg-red-500' : 'bg-purple-600'}`}>{p.badge}</span>}
                  <div>
                    <img src={p.img} alt={p.name} class={`w-full aspect-square object-cover rounded-lg mb-3 ${p.stock === 0 ? 'grayscale opacity-60' : ''}`} />
                    <h3 class="font-bold text-sm mb-1">{p.name}</h3>
                    <div class="text-cyan-400 font-bold mb-1">{p.price}฿</div>
                    <div class="text-xs text-slate-400 mb-3">เหลือ {p.stock} ชิ้น</div>
                  </div>
                  <button disabled={p.stock === 0} class={`w-full py-2 rounded-lg font-bold text-sm ${p.stock > 0 ? 'bg-emerald-500 text-white' : 'bg-slate-700 text-slate-500 cursor-not-allowed'}`}>
                    {p.stock > 0 ? '🛒 ซื้อสินค้า' : '📦 สินค้าหมด'}
                  </button>
                </div>
              ))}
            </div>
          </div>
        </div>
      );
    }
    ReactDOM.render(<App />, document.getElementById('root'));
  </script>
</body>
</html>
