# Tailwind CSS Cheatsheet

## **1. Layout**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `container`            | Center content with padding       | `<div class="container mx-auto">` |
| `box-border` / `box-content` | Set box-sizing                 | `box-border`                   |
| `block` / `inline-block` / `inline` | Display types            | `<div class="block">`          |
| `hidden`               | Hide an element                   | `<div class="hidden">`         |
| `flex` / `grid`        | Display flex/grid                 | `<div class="flex">`           |
| `items-center`         | Align items vertically in flexbox | `<div class="flex items-center">` |
| `justify-between`      | Align items horizontally          | `<div class="flex justify-between">` |

---

## **2. Spacing**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `p-{n}`               | Padding (`n` = 0, 1, 2, etc.)     | `p-4` (padding 1rem)           |
| `m-{n}`               | Margin (`n` = 0, 1, 2, etc.)      | `m-4` (margin 1rem)            |
| `space-x-{n}`         | Horizontal spacing between items   | `<div class="space-x-4">`      |
| `space-y-{n}`         | Vertical spacing between items     | `<div class="space-y-4">`      |

---

## **3. Sizing**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `w-{value}`           | Width (e.g., `1/2`, `full`, etc.)  | `w-1/2`                        |
| `h-{value}`           | Height (e.g., `screen`, `full`)    | `h-screen`                     |
| `max-w-{value}`       | Max width                          | `max-w-lg`                     |
| `min-h-{value}`       | Min height                         | `min-h-screen`                 |

---

## **4. Colors**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `bg-{color}`          | Background color                  | `bg-blue-500`                  |
| `text-{color}`        | Text color                        | `text-gray-800`                |
| `border-{color}`      | Border color                      | `border-red-500`               |
| `hover:bg-{color}`    | Hover background color            | `hover:bg-green-600`           |

---

## **5. Borders and Shadows**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `border`              | Add a border                      | `border`                       |
| `border-{size}`       | Border width                      | `border-2`                     |
| `rounded-{size}`      | Border radius                     | `rounded-lg`                   |
| `shadow-{size}`       | Box shadow                        | `shadow-md`                    |

---

## **6. Typography**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `text-{size}`         | Font size                         | `text-lg`                      |
| `font-{weight}`       | Font weight                       | `font-bold`                    |
| `leading-{value}`     | Line height                       | `leading-relaxed`              |
| `tracking-{value}`    | Letter spacing                    | `tracking-wider`               |

---

## **7. Flexbox and Grid**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `flex` / `inline-flex` | Flex container                   | `flex`                         |
| `flex-row` / `flex-col`| Direction of flex items           | `flex-row`                     |
| `gap-{n}`             | Space between grid/flex items     | `gap-4`                        |
| `grid-cols-{n}`       | Define grid columns               | `grid-cols-3`                  |

---

## **8. Interactivity**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `hover:{utility}`      | Hover state                       | `hover:bg-blue-500`            |
| `focus:{utility}`      | Focus state                       | `focus:outline-none`           |
| `active:{utility}`     | Active state                      | `active:bg-red-600`            |

---

## **9. Positioning**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `relative` / `absolute` / `fixed` | Set position           | `absolute`                     |
| `top-{value}`          | Top offset                       | `top-4`                        |
| `z-{value}`            | Z-index                          | `z-50`                         |

---

## **10. Breakpoints**
| Utility                | Description                        | Example                         |
|------------------------|------------------------------------|---------------------------------|
| `sm:{utility}`         | Apply on small screens            | `sm:text-base`                 |
| `md:{utility}`         | Apply on medium screens           | `md:p-4`                       |
| `lg:{utility}`         | Apply on large screens            | `lg:bg-red-500`                |
| `xl:{utility}`         | Apply on extra-large screens      | `xl:flex`                      |
| `2xl:{utility}`        | Apply on 4K screens               | `2xl:grid-cols-6`              |

---
