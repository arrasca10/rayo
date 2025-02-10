import { useState } from "react";
import { motion } from "framer-motion";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Plane, MapPin, Calendar } from "lucide-react";

export default function HomePage() {
  const [search, setSearch] = useState({ from: "", to: "", date: "" });

  return (
    <div className="min-h-screen bg-gray-100 text-gray-900">
      {/* Navbar */}
      <nav className="bg-gray-900 text-white p-4 flex justify-between items-center">
        <h1 className="text-2xl font-bold text-orange-500">Rayo Linhas Aéreas</h1>
        <ul className="flex gap-6">
          <li className="hover:text-orange-500 cursor-pointer">Home</li>
          <li className="hover:text-orange-500 cursor-pointer">Destinos</li>
          <li className="hover:text-orange-500 cursor-pointer">Contato</li>
        </ul>
      </nav>
      
      {/* Hero Section */}
      <header className="h-[60vh] bg-gray-700 flex items-center justify-center">
        <motion.div
          initial={{ opacity: 0, y: -20 }}
          animate={{ opacity: 1, y: 0 }}
          className="text-center text-white"
        >
          <h2 className="text-4xl font-bold">Explore o mundo com conforto e segurança</h2>
          <p className="mt-2">Encontre as melhores ofertas de voos para qualquer destino.</p>
        </motion.div>
      </header>
      
      {/* Search Section */}
      <section className="p-6 max-w-4xl mx-auto bg-white shadow-lg -mt-16 rounded-2xl relative">
        <div className="flex gap-4">
          <Input
            icon={<MapPin size={20} />}
            placeholder="Origem"
            value={search.from}
            onChange={(e) => setSearch({ ...search, from: e.target.value })}
          />
          <Input
            icon={<Plane size={20} />}
            placeholder="Destino"
            value={search.to}
            onChange={(e) => setSearch({ ...search, to: e.target.value })}
          />
          <Input
            icon={<Calendar size={20} />}
            type="date"
            value={search.date}
            onChange={(e) => setSearch({ ...search, date: e.target.value })}
          />
          <Button className="bg-orange-500 text-white px-4 py-2 rounded-lg">Buscar</Button>
        </div>
      </section>
      
      {/* Popular Destinations */}
      <section className="p-10 text-center">
        <h3 className="text-3xl font-bold text-gray-900">Destinos Populares</h3>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mt-6">
          {[
            { city: "Rio de Janeiro", image: "/rio.jpg" },
            { city: "São Paulo", image: "/sp.jpg" },
            { city: "Salvador", image: "/salvador.jpg" }
          ].map((dest, index) => (
            <Card key={index}>
              <CardContent>
                <img src={dest.image} alt={dest.city} className="rounded-lg h-40 w-full object-cover" />
                <h4 className="text-lg font-semibold mt-2">{dest.city}</h4>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>
      
      {/* Footer */}
      <footer className="bg-gray-900 text-white text-center p-4 mt-10">
        <p>&copy; 2025 Rayo Linhas Aéreas. Todos os direitos reservados.</p>
      </footer>
    </div>
  );
}
