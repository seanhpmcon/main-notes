When doing pagination server-side, the main idea to to have a link tag with the button components that would render the the page required when the button is clicked. Essentially the state of the page that determines what data is rendered would be passed in the URL. For the example used, a page parameter is added to the URL that specifies the number of the page. Therefore if the current page is 10, the next button would contain a URL with page parameter set as 11 and the previous button would be 9. The data fetch aspect would contain the logic to get the data corresponding to the page number defined.

The Pagination button file:
```jsx
"use client";

import Link from "next/link";
import { usePathname, useSearchParams } from "next/navigation";

import { BsChevronLeft, BsChevronRight } from "react-icons/bs";

export default function PaginationButtons() {
  const pathname = usePathname();
  const searchParams = useSearchParams();
  const startIndex = +searchParams.get("page") || 0;
  return (
    <div className="text-blue-700 flex px-10 pb-4 justify-between sm:justify-start sm:space-x-44 sm:px-0">
      {startIndex >= 1 && (
        <Link href={`${pathname}?page=${startIndex - 1}`} >
          <div className="flex flex-col cursor-pointer items-center hover:underline">
            <BsChevronLeft className="h-5" />
            <p>Previous</p>
          </div>
        </Link>
      )}
      {startIndex <= 90 && (
        <Link
          href={`${pathname}?page=${startIndex + 1}`}
        >
          <div className="flex flex-col cursor-pointer items-center hover:underline">
            <BsChevronRight className="h-5" />
            <p>Next</p>
          </div>
        </Link>
      )}
    </div>
  );
}
```

The page where the data would be displayed:
```jsx
import PaginationButtons from "@/components/PaginationButtons";

export default async function Home({searchParams}) {

    const page = searchParams.page || '0';

    const jdata = await fetch(`http://localhost:3000/api/user?page=${page}`, { cache: 'no-store' });
    const data = await jdata.json();

  return (
      <div>
          {data.map((user, index) => {
              return <div className='flex items-center justify-center' key={index}>
                  <div className='h-32 w-96' key={index}>
                      <div className='flex items-center justify-center rounded-md bg-slate-400 h-full' key={index}>{user.id}</div>
                  </div>
              </div>
          })}
        {/* add links to the buttons when clicked */}
      <PaginationButtons/>
      </div>
  )
}
```

The API route where the data is fetched:
```jsx
import {getProducts} from '../../data'

export async function GET(req, res) {
    const urlParams = new URLSearchParams(req.url);
    const page = +urlParams.get('http://localhost:3000/api/product?page');
    const data = await getProducts(page);
    return new Response(JSON.stringify(data))
}
```

In this example, when you go to the page URL, data is fetch for page zero, and only the next button is rendered with a link to the page URL along with the page variable defined as 1.