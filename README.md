# unsolved-mysteries-site-# 🕵🏽 Unsolved Mysteries & History

A vintage-themed interactive website exploring the world’s most fascinating unsolved mysteries, legends, and historical enigmas.  
Built with **React, TailwindCSS, Framer Motion**, and deployed on **GitHub Pages**.  

✨ Created by **Akosua Addae Buapim**  

---

## 🌍 Live Demo
🔗 [Click here to visit the site](https://YOUR_akosuaaddaebuapim-hash.github.io/unsolved-mysteries-site/)  

---

## 🧩 Features
- 📜 **Vintage Brown Theme** for an old-world vibe  
- 🔍 **Search & Filter** to explore mysteries quickly  
- 📂 **Expandable Cards** with more details on each case  
- 🎭 **Smooth Animations** with Framer Motion  
- 🎲 **Mystery of the Day** generator (optional extra)  
- 👩🏽‍💻 **Credit Footer**: Built by Akosua Addae Buapim  

---

## 🚀 Tech Stack
- [React](https://reactjs.org/) – UI Framework  
- [TailwindCSS](https://tailwindcss.com/) – Styling  
- [Framer Motion](https://www.framer.com/motion/) – Animations  
- [Vite](https://vitejs.dev/) – Fast build tool  
- [GitHub Pages](https://pages.github.com/) – Hosting  

---

## 🛠️ Installation & Setup

1. **Clone the repo**  
   ```bash
   git clone https://github.com/akosuaaddaebuapim-hash/unsolved-mysteries-site.git
   cd unsolved-mysteries-site
   import React, { useState, useEffect } from "react"; import { motion } from "framer-motion"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

// --- Mysteries Data --- const mysteries = [ { title: "The Lost City of Atlantis", description: "A legendary island said to have sunk beneath the ocean, never to be found again.", }, { title: "The Voynich Manuscript", description: "An illustrated codex written in an unknown language, baffling experts for centuries.", }, { title: "The Bermuda Triangle", description: "A region in the Atlantic Ocean where ships and planes mysteriously disappear.", }, { title: "Jack the Ripper", description: "The infamous serial killer who terrorized London in 1888 and was never caught.", }, { title: "Stonehenge", description: "An ancient stone circle in England whose purpose and construction remain debated.", }, { title: "The Phaistos Disc", description: "A clay disc from Crete with mysterious symbols no one has been able to decipher.", }, { title: "The Wow! Signal", description: "A strong radio signal detected in 1977 from outer space, never heard again.", }, ];

export default function MysterySite() { const [mystery, setMystery] = useState(null);

// Pick a mystery based on today's date (so it's the same mystery for everyone daily) useEffect(() => { const today = new Date(); const dayOfYear = Math.floor( (today - new Date(today.getFullYear(), 0, 0)) / 1000 / 60 / 60 / 24 ); const index = dayOfYear % mysteries.length; setMystery(mysteries[index]); }, []);

// Manual reshuffle (optional fun) const reshuffleMystery = () => { const randomIndex = Math.floor(Math.random() * mysteries.length); setMystery(mysteries[randomIndex]); };

return ( <div className="min-h-screen bg-amber-100 text-brown-900 font-serif p-6"> <header className="text-center mb-10"> <h1 className="text-4xl font-bold mb-2">🕵🏽 Unsolved Mysteries & History</h1> <p className="text-lg italic">Step into the unknown with stories that still puzzle humanity...</p> </header>

{/* --- Mystery of the Day Section --- */}
  <section className="mb-10 text-center">
    <h2 className="text-2xl font-semibold mb-4">✨ Mystery of the Day</h2>
    {mystery && (
      <motion.div
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.6 }}
        className="max-w-lg mx-auto"
      >
        <Card className="bg-amber-200 border border-amber-400 shadow-xl rounded-2xl">
          <CardContent className="p-6">
            <h3 className="text-xl font-bold mb-2">{mystery.title}</h3>
            <p className="text-md mb-4">{mystery.description}</p>
            <Button onClick={reshuffleMystery} className="bg-amber-600 text-white hover:bg-amber-700">
              🔄 Shuffle Mystery
            </Button>
          </CardContent>
        </Card>
      </motion.div>
    )}
  </section>

  {/* --- All Mysteries List --- */}
  <section>
    <h2 className="text-2xl font-semibold text-center mb-6">📜 Explore More Mysteries</h2>
    <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
      {mysteries.map((m, index) => (
        <motion.div
          key={index}
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.5, delay: index * 0.1 }}
        >
          <Card className="bg-amber-50 border border-amber-300 shadow-lg rounded-2xl">
            <CardContent className="p-4">
              <h3 className="text-lg font-bold mb-2">{m.title}</h3>
              <p className="text-sm">{m.description}</p>
            </CardContent>
          </Card>
        </motion.div>
      ))}
    </div>
  </section>

  {/* Footer */}
  <footer className="text-center mt-16 text-sm text-brown-700 italic">
    ✨ Created by Akosua Addae Buapim
  </footer>
</div>

); }


