---
title: "Cards"
description: ""
summary: ""
date: 2025-02-01T15:01:31+05:30
lastmod: 2025-02-01T15:01:31+05:30
draft: false
weight: 1004
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

```js {title="Cards.jsx" lineNos=true}
import React from 'react';
import { FaShoppingCart, FaHeart, FaStar } from 'react-icons/fa';

const products = [
  {
    id: 1,
    image: "https://via.placeholder.com/300",
    name: "Sample Product 1",
    description: "This is the description of product 1 that is dynamically truncated.",
    price: 100.0,
    discount: 20,
    category: "Electronics",
    subcategory: "Smartphones",
    rating: 4.5,
    reviews: 120,
  },
  {
    id: 2,
    image: "https://via.placeholder.com/300",
    name: "Sample Product 2",
    description: "This is the description of product 2, which is also dynamically truncated.",
    price: 150.0,
    discount: 15,
    category: "Home Appliances",
    subcategory: "Kitchen",
    rating: 4.0,
    reviews: 85,
  },
  {
    id: 3,
    image: "https://via.placeholder.com/300",
    name: "Sample Product 3",
    description: "This description for product 3 showcases truncation in a professional UI.",
    price: 200.0,
    discount: 10,
    category: "Fashion",
    subcategory: "Clothing",
    rating: 3.8,
    reviews: 50,
  },
  {
    id: 4,
    image: "https://via.placeholder.com/300",
    name: "Sample Product 4",
    description: "This is product 4's description for showcasing professional spacing.",
    price: 250.0,
    discount: 25,
    category: "Sports",
    subcategory: "Fitness",
    rating: 4.7,
    reviews: 200,
  },
  {
    id: 5,
    image: "https://via.placeholder.com/300",
    name: "Sample Product 5",
    description: "Here is the description for product 5, professionally styled.",
    price: 300.0,
    discount: 30,
    category: "Books",
    subcategory: "Fiction",
    rating: 4.9,
    reviews: 150,
  },
];

const Cards = () => {
  return (
    <div className="min-h-screen  p-6 font-sans">
      <h1 className="text-3xl font-extrabold text-center mb-8 tracking-wide">
        Explore Our Products
      </h1>
      <div className="grid gap-8 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 max-w-7xl mx-auto">
        {products.map((product) => {
          const discountedPrice = product.price - (product.price * product.discount) / 100;

          return (
            <div
              key={product.id}
              className="bg-white border border-gray-200 rounded-lg shadow-lg hover:shadow-2xl transition-shadow duration-300 transform hover:scale-105"
            >
              <div className="relative">
                <img
                  className="w-full h-56 object-cover rounded-t-lg transition-all duration-500 transform hover:scale-110"
                  src={product.image}
                  alt={product.name}
                />

                <div className="absolute bottom-3 right-3 flex flex-col space-y-3">
                  <button
                    className="text-gray-500 hover:text-red-500 transition duration-300 transform hover:scale-110"
                    title="Add to Wishlist"
                  >
                    <FaHeart size={20} />
                  </button>
                  <button
                    className="text-gray-500 hover:text-blue-500 transition duration-300 transform hover:scale-110"
                    title="Add to Cart"
                  >
                    <FaShoppingCart size={20} />
                  </button>
                </div>
              </div>

              <div className="p-5">
                <div className="flex space-x-2 mb-3">
                  <span className="bg-blue-500 text-white text-xs font-medium px-3 py-1 rounded-full shadow-md">
                    {product.category}
                  </span>
                  <span className="bg-gray-500 text-white text-xs font-medium px-3 py-1 rounded-full shadow-md">
                    {product.subcategory}
                  </span>
                </div>

                <h2 className="text-xl font-semibold text-gray-800 truncate mb-2 hover:text-blue-500">
                  {product.name}
                </h2>
                <p className="text-sm text-gray-600 mt-2 truncate">{product.description}</p>
                
                <div className="flex items-center mt-3">
                  <FaStar className="text-yellow-400" />
                  <span className="text-sm text-gray-600 ml-2">
                    {product.rating.toFixed(1)} 
                    <span className="ml-1 text-gray-500">({product.reviews} reviews)</span>
                  </span>
                </div>

                <div className="mt-4 flex justify-between items-center">
                  <div className="flex items-center space-x-3">
                    <p className="text-lg font-semibold text-gray-900">
                      ${discountedPrice.toFixed(2)}
                    </p>
                    <p className="text-sm text-gray-500 line-through">
                      ${product.price.toFixed(2)}
                    </p>
                    <p className="text-sm text-green-500 font-medium">
                      Save {product.discount}%
                    </p>
                  </div>
                </div>
              </div>
            </div>
          );
        })}
      </div>
    </div>
  );
};

export default Cards;

```