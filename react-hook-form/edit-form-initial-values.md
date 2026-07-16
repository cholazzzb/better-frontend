# Edit Form, for initial values

## Worse

```tsx
function Form() {
  const { reset } = useForm();

  useEffect(() => {
    reset(yourQuery.data);
  }, [yourQuery.data, reset]);

  //....Your form component
}
```

- Double Renders
- Boilerplate

## Better

```tsx
function Form() {
  /**
   * For example using react-query or RTK Query
   */
  const yourQuery = useYourQuery();

  const methods = useForm({
    values: yourQuery.data || {}, // Pass initial values from query (async data)
  });

  //....Your form component
}
```

- Single Render
- Automatic Syncing

[Link to Reference](https://react-hook-form.com/docs/useform#values)
