---
title: "Carousel"
description: ""
summary: ""
date: 2025-02-01T15:02:36+05:30
lastmod: 2025-02-01T15:02:36+05:30
draft: false
weight: 1005
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

```js {title="Carousel.jsx" lineNos=true}
import React, { useState, useEffect, useRef } from "react";

const Carousel = () => {
  const images = [
    "https://via.placeholder.com/800x400?text=Slide+1",
    "https://via.placeholder.com/800x400?text=Slide+2",
    "https://via.placeholder.com/800x400?text=Slide+3",
    "https://via.placeholder.com/800x400?text=Slide+4",
  ];

  const [isTransitioning, setIsTransitioning] = useState(false);
  const [currentIndex, setCurrentIndex] = useState(0);
  const carouselRef = useRef(null);

  useEffect(() => {
    const interval = setInterval(() => {
      moveToNext();
    }, 3000);

    return () => clearInterval(interval);
  }, []);

  const moveToNext = () => {
    if (!carouselRef.current) return;
    setIsTransitioning(true);
    carouselRef.current.style.transition = "transform 0.7s ease-in-out";
    carouselRef.current.style.transform = `translateX(-100%)`;

    setTimeout(() => {
      const firstChild = carouselRef.current.children[0];
      carouselRef.current.appendChild(firstChild);
      carouselRef.current.style.transition = "none";
      carouselRef.current.style.transform = "translateX(0)";
      setIsTransitioning(false);
      setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
    }, 700);
  };

  const moveToPrevious = () => {
    if (!carouselRef.current) return;
    const lastChild =
      carouselRef.current.children[carouselRef.current.children.length - 1];
    carouselRef.current.prepend(lastChild);
    carouselRef.current.style.transition = "none";
    carouselRef.current.style.transform = "translateX(-100%)";

    setTimeout(() => {
      carouselRef.current.style.transition = "transform 0.7s ease-in-out";
      carouselRef.current.style.transform = "translateX(0)";
      setCurrentIndex(
        (prevIndex) => (prevIndex - 1 + images.length) % images.length
      );
    }, 50);
  };

  const handleDotClick = (index) => {
    if (!carouselRef.current || index === currentIndex) return;

    const moveBy = index - currentIndex;
    if (moveBy > 0) {
      for (let i = 0; i < moveBy; i++) {
        moveToNext();
      }
    } else {
      for (let i = 0; i < -moveBy; i++) {
        moveToPrevious();
      }
    }
  };

  return (
    <div className="relative w-full max-w-full mx-auto overflow-hidden bg-gray-100 shadow-lg border-2 border-yellow-500">
      {/* Image Slider */}
      <div
        ref={carouselRef}
        className="flex transition-transform duration-700"
        style={{
          display: "flex",
        }}
      >
        {images.map((image, idx) => (
          <div key={idx} className="w-full flex-shrink-0">
            <img
              src={image}
              alt={`Slide ${idx + 1}`}
              className="w-full object-cover h-[30vh] sm:h-[50vh]" // 30vh for mobile, 40vh for larger screens
            />
          </div>
        ))}
      </div>

      {/* Dot Indicators */}
      <div className="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-3">
        {images.map((_, idx) => (
          <button
            key={idx}
            onClick={() => handleDotClick(idx)}
            className={`w-4 h-4 rounded-full transition-colors duration-300 ${
              idx === currentIndex ? "bg-blue-500" : "bg-gray-300"
            }`}
          ></button>
        ))}
      </div>

      {/* Navigation Buttons */}
      <button
        onClick={moveToPrevious}
        className="absolute left-4 top-1/2 transform -translate-y-1/2 text-gray-700 hover:text-gray-900 p-2 rounded-full transition-all duration-300 group"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          className="w-6 h-6 group-hover:scale-110 transform transition-transform"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          strokeWidth="2"
        >
          <path
            strokeLinecap="round"
            strokeLinejoin="round"
            d="M15 19l-7-7 7-7"
          />
        </svg>
      </button>
      <button
        onClick={moveToNext}
        className="absolute right-4 top-1/2 transform -translate-y-1/2 text-gray-700 hover:text-gray-900 p-2 rounded-full transition-all duration-300 group"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          className="w-6 h-6 group-hover:scale-110 transform transition-transform"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          strokeWidth="2"
        >
          <path strokeLinecap="round" strokeLinejoin="round" d="M9 5l7 7-7 7" />
        </svg>
      </button>
    </div>
  );
};

export default Carousel;

```