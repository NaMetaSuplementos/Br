# Br
Somos uma loja voltada a produtos de suplementos e outros 
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { useState } from "react";
import { ShoppingCart, Search } from "lucide-react";

const products = [
  {
    id: 1,
    name: "Whey Protein",
    price: "R$150,00",
    image: "https://cdn.awsli.com.br/600x450/2449/2449077/produto/209775379/2a3487a92e.jpg",
  },
  {
    id: 2,
    name: "Creatina Monohidratada",
    price: "R$90,00",
    image: "https://static.lojanutrifit.com.br/produtos/creatina-monohidratada-creapure-250g-creapure-growth-supplements/01.jpg",
  },
  {
    id: 3,
    name: "BCAA 4:1:1",
    price: "R$75,00",
    image: "https://www.integralmedica.com.br/media/catalog/product/b/c/bcaa-411-100-caps-integralmedica_1.jpg",
  },
];

export default function LojaDeSuplementos() {
  const [search, setSearch] = useState("");

  const filteredProducts = products.filter((product) =>
    product.name.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div className="p-4 max-w-screen-xl mx-auto">
      <header className="flex justify-between items-center py-6">
        <h1 className="text-3xl font-bold text-blue-600">Suplementos Power</h1>
        <ShoppingCart className="w-6 h-6 text-gray-700" />
      </header>

      <div className="flex items-center gap-2 mb-6">
        <Search className="w-5 h-5 text-gray-500" />
        <Input
          type="text"
          placeholder="Buscar suplementos..."
          value={search}
          onChange={(e) => setSearch(e.target.value)}
          className="w-full max-w-md"
        />
      </div>

      <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
        {filteredProducts.map((product) => (
          <Card key={product.id} className="rounded-2xl shadow-md">
            <img
              src={product.image}
              alt={product.name}
              className="w-full h-48 object-cover rounded-t-2xl"
            />
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold text-gray-800">
                {product.name}
              </h2>
              <p className="text-blue-600 font-bold mt-2">{product.price}</p>
              <Button className="mt-4 w-full">Adicionar ao carrinho</Button>
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}

