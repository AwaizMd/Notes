# Tailwind CSS Responsive Design Cheatsheet

| **Feature**       | **Mobile<br>(Default)** | **Tablet<br>(`sm:`)** | **Small Laptop<br>(`md:`)** | **Large Laptop<br>(`lg:`)** | **Desktop<br>(`xl:`)** | **TV/4K<br>(`2xl:`)** |
|--------------------|-------------------------|------------------------|-----------------------------|-----------------------------|-------------------------|------------------------|
| **Text Size**      | `text-sm`              | `sm:text-base`         | `md:text-lg`               | `lg:text-xl`               | `xl:text-2xl`          | `2xl:text-3xl`         |
| **Padding**        | `p-2`                 | `sm:p-4`              | `md:p-6`                   | `lg:p-8`                   | `xl:p-10`              | `2xl:p-12`            |
| **Margin**         | `m-2`                 | `sm:m-4`              | `md:m-6`                   | `lg:m-8`                   | `xl:m-10`              | `2xl:m-12`            |
| **Width**          | `w-full`              | `sm:w-3/4`            | `md:w-1/2`                 | `lg:w-1/3`                 | `xl:w-1/4`             | `2xl:w-1/6`           |
| **Height**         | `h-auto`              | `sm:h-64`             | `md:h-80`                  | `lg:h-96`                  | `xl:h-screen`          | `2xl:h-full`          |
| **Display**        | `block`               | `sm:inline-block`      | `md:flex`                  | `lg:grid`                  | `xl:hidden`            | `2xl:block`           |
| **Flexbox**        | `flex-col`            | `sm:flex-row`          | `md:gap-4`                 | `lg:gap-6`                 | `xl:gap-8`             | `2xl:gap-10`          |
| **Grid Columns**   | `grid-cols-1`         | `sm:grid-cols-2`       | `md:grid-cols-3`           | `lg:grid-cols-4`           | `xl:grid-cols-5`       | `2xl:grid-cols-6`     |
| **Alignment**      | `items-start`         | `sm:items-center`      | `md:items-end`             | `lg:justify-center`        | `xl:justify-end`       | `2xl:justify-between` |
| **Background**     | `bg-gray-100`         | `sm:bg-gray-200`       | `md:bg-gray-300`           | `lg:bg-gray-400`           | `xl:bg-gray-500`       | `2xl:bg-gray-600`     |
| **Border Width**   | `border`              | `sm:border-2`          | `md:border-4`              | `lg:border-8`              | `xl:border-t`          | `2xl:border-b`        |

## Example Usage
```html
<div class="text-sm sm:text-base md:text-lg lg:text-xl xl:text-2xl 2xl:text-3xl 
            p-2 sm:p-4 md:p-6 lg:p-8 xl:p-10 2xl:p-12 
            w-full sm:w-3/4 md:w-1/2 lg:w-1/3 xl:w-1/4 2xl:w-1/6 
            bg-gray-100 sm:bg-gray-200 md:bg-gray-300 lg:bg-gray-400 xl:bg-gray-500 2xl:bg-gray-600 
            flex flex-col sm:flex-row md:gap-4 lg:gap-6 xl:gap-8 2xl:gap-10">
  Responsive Example
</div>
