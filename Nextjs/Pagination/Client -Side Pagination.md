In the client-side pagination, the same fetch API is used with the same page variable but every time the buttons are click a function is run instead of redirecting to a link. This button updates a page variable that gets sent to the API endpoint to fetch the data. The react hooks useEffect and useState are used to fetch and store the data.

```jsx
'use client'

import { useEffect, useState } from "react";

const EffectPagination = () => {
  const [page, setPage] = useState(0);
  const [data, setData] = useState([]);

  const fetchData = async () => {
    try {
      const response = await fetch(`http://localhost:3000/api/user?page=${page}`);
      const jdata = await response.json();
      setData(jdata);
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  };

  useEffect(() => {
    fetchData();
  }, [page]);

  const handleIncrement = () => {
    setPage(page + 1);
  };

  const handleDecrement = () => {
    setPage(page - 1);
  };

  return (
    <div>
      {data.map((user, index) => (
        <div className='flex items-center justify-center' key={index}>
          <div className='h-32 w-96' key={index}>
            <div className='flex items-center justify-center rounded-md bg-slate-400 h-full' key={index}>
              {user.id}
            </div>
          </div>
        </div>
      ))}
      {/* Add links to the buttons when clicked */}
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  );
};

export default EffectPagination;
```

And the API:
```jsx
import {getProducts} from '../../data'

export async function GET(req, res) {
    const urlParams = new URLSearchParams(req.url);
    const page = +urlParams.get('http://localhost:3000/api/product?page');
    const data = await getProducts(page);
    return new Response(JSON.stringify(data))
}
```

In the example above, when the buttons are clicked, they trigger a function that either adds one to the page variable for next or subtracts one for the previous page. This would trigger the setPage function and change the value of the page variable which would trigger the useEffect function that would make a fetch to the API and change the data variable which hold the data for the page render and would then trigger a re-render of the page to update it with the new data.