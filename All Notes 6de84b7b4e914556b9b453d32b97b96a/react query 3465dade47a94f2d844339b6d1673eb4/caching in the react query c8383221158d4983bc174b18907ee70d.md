# caching in the react query

useQuery provide the facility of the caching the data and the default time is the 5 minutes. useQuery also return the values like isFetching, refetch(method). where isFetching is used to check whether reactQuery fetching the data in the background or not while refetch is used to fetch data on the perticular event. caching has many scenarios so the useQuery accept {} as a third argument which has the set of values. values are →

cacheTime(default 5 mint) →it is the state where your cache data is persist after that period of the time data get vanished.

staleTime(default 0) → in the stale time it never fetch data and use old data to render once stale time end it render new data after the fetch.

refetchOnMount(default true, false, ‘always’) → it refetch data each time component get mount.

refetchOnWindowFocus(default true, false, ‘always’) → each time window is focused.

reactQuery also provide the polling that is the refetch after every set of the interval that is 

refetchInterval(default false)→it refetch after set of the interval. i
refetchIntervalBackground(default false) →it also same as refetchInterval but a diference is is refetch tabs and windows even when they are not focused.

we alse use enabled property to not fetch the immediately.

```jsx
const cachingProperties = {
			cacheTime: 30000,
      staleTime: 10,
      refetchOnMount: true,
			refetchOnWindowFocus: true,
      refetchInterval: false,
			refetchIntervalBackground: false,
			enabled: false
 }

const {isFetching, refetch} = useQuery(id, cb, cachingProperties)

if (isLoading || isFetching) {
    return <h2>Loading...</h2>;
  }

<button onClick={refetch}>Fetch Heroes</button>
```

after fetching the data we has the scenarios like success, error or the transformation of the data after success reactQuery also provide a way to deal with.

in the object it takes keys as

```jsx
const onSuccess = (data) => {
    console.log('Data successfully fetch', data);
  };

const onError = (err) => {
    console.log("OOP's Error", err);
  };

{
      onSuccess,
      onError,
      select: (data) => {
        const names = data.data.map(eachHero => eachHero.name);
        return names;
}
```

we can use the inititalData to not fetch always. 

```jsx
{
      initialData: (data) => {
        const cachedData = useQueryClient().getQueryData(id);
        return cachedData;
}

```