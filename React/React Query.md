Installation
```
npm i @tanstack/react-query

import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <App />
    </QueryClientProvider>
  )
}
```

```
"use client";

import { useQuery } from "@tanstack/react-query";
import { useState } from "react";

const BASE_URL = "https://jsonplaceholder.typicode.com";

interface Post {
  id: number;
  title: string;
}

export default function FetchExample2() {
  const [page, setPage] = useState(0);

  const {
    data: posts,
    isError,
    isPending,
  } = useQuery({
    queryKey: ["posts", { page }],
    staleTime: 1000,
    queryFn: async () => {
      const response = await fetch(`${BASE_URL}/posts?page=${page}`);
      return (await response.json()) as Post[];
    },
  });

  // Do cool things with the JSX

  return (
    <div className="tutorial">
      <h1 className="mb-4 text-2xl">Data Fething in React</h1>
      <button onClick={() => setPage(page - 1)}>Decrease Page ({page})</button>
      <button onClick={() => setPage(page + 1)}>Increase Page ({page})</button>
      {isPending && <div>Loading...</div>}
      {!isPending && (
        <ul>
          {posts?.map((post) => {
            return <li key={post.id}>{post.title}</li>;
          })}
        </ul>
      )}
    </div>
  );
}
```