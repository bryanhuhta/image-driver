# image-driver

## Model

The database model is defined by `Metadata`.

```python
class Metadata(NamedTuple):
    id: Optional[int] = None
    number: Optional[int] = None
    group: Optional[int] = None
    min_image_index: Optional[int] = None
    max_image_index: Optional[int] = None
```

To augment this model, add additional fields. They should have a default value of `None`.

## Database

The driver interface is fairly straightforward.

- `Database(path: str)`: creates a new database connection (and a new database entirely if it doesn't exist). The database file will be stored at `path`. use `:memory:` for an in-memory database.
- `add(m: Metadata) -> Metadata`: adds a metadata model to the database, returning the inserted values.
- `get(id: int) -> Metadata`: gets a metadata model from the database, by id.
- `update(id: int, m: Metadata) -> Metadata`: updates a metadata model in the database. Just the values in `m` that are not `None` are updated.
- `delete(id: int)`: deletes a metadata model from the database.

Additional methods can be added to this interface to support more complicated filters.
