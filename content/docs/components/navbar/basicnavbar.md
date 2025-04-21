---
title: "Basic Navbar"
description: ""
summary: ""
date: 2025-02-01T13:56:25+05:30
lastmod: 2025-02-01T13:56:25+05:30
draft: false
weight: 1003
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


```js {title="BasicNavbar.jsx" lineNos=true}
import React, { useState } from "react";
import { CiHome, CiCircleList, CiUser, CiHeadphones } from "react-icons/ci";

const BasicNavbar = () => {
  const [isDrawerOpen, setIsDrawerOpen] = useState(false);

  const navigation_menu = [
    {
      menu_title: "Home",
      url_path: "/",
      menu_icon: <CiHome />,
    },
    {
      menu_title: "Project",
      url_path: "/project",
      menu_icon: <CiCircleList />,
    },
    {
      menu_title: "About",
      url_path: "/about",
      menu_icon: <CiUser />,
    },
    {
      menu_title: "Contact",
      url_path: "/contact",
      menu_icon: <CiHeadphones />,
    },
  ];

  return (
    <>
      <nav className="flex justify-between px-6 py-3 box-border w-full bg-gradient-to-r from-white/10 via-white/20 to-white/10 backdrop-blur-xl border-b border-white/20 shadow-lg text-xl">
        <div>Logo</div>

        <div className="md:hidden flex items-center">
          <button
            className="text-3xl focus:outline-none"
            onClick={() => setIsDrawerOpen(true)}
          >
            &#9776;
          </button>
        </div>

        <div className="hidden md:flex items-center">
          <ul className="flex space-x-6">
            {navigation_menu.map((menu_item, index_value) => {
              return (
                <li key={index_value}>
                  <a href={menu_item.url_path} className="flex items-center">
                    <span className="px-1">{menu_item.menu_icon}</span>
                    {menu_item.menu_title}
                  </a>
                </li>
              );
            })}
          </ul>
        </div>

        <div className="hidden md:block">Login</div>
      </nav>

      {isDrawerOpen && (
        <div
          className="fixed inset-0 bg-black/50 backdrop-blur-sm z-40"
          onClick={() => setIsDrawerOpen(false)}
        ></div>
      )}

      <div
        className={`fixed top-0 left-0 h-full w-4/5 bg-gray-900 text-white transform ${
          isDrawerOpen ? "translate-x-0" : "-translate-x-full"
        } transition-transform duration-300 ease-in-out z-50`}
      >
        <ul className="mt-10 space-y-6">
          {navigation_menu.map((menu_item, index_value) => {
            return (
              <li key={index_value} className="px-6">
                <a
                  href={menu_item.url_path}
                  className="flex items-center space-x-2"
                >
                  <span>{menu_item.menu_icon}</span>
                  {menu_item.menu_title}
                </a>
              </li>
            );
          })}
        </ul>
      </div>
    </>
  );
};

export default BasicNavbar;

```