# Hydration Failed in certain component in Nextjs 14

## Cause of Hydration Error

- All component in nextjs are first served as server side component which cause hydration error

- react leaflet or jquery etc trigger window object on server side , as window object is not available in server component when rendering cause hydration error mostly

## Common fix

- Invalid jsx like div inside p tag

- Using condition like typeof window !== 'undefined' and localStorage in jsx or rendering

- Calling useEffect conditionally or incorrect order of hooks

# Fix

- Default import component and disable SSR (server side rendering) for that component

  ```javascript
  const CSR = dynamic(() => import("@/components/MapMarker/index"), {
    ssr: false,
  });

  const Home = () => {
    return (
      <>
        <CSR />
      </>
    );
  };
  ```
