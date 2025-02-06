Simple benchmark for comparing different dataclass-like providers.

Fully works only up to Python 3.12.
Does not work with Python 3.13 (yet), due to inaccuracies with Pympler for calculating the memory usage.

Adapted from https://github.com/mCodingLLC/VideosSampleCode/blob/master/videos/079_which_dataclass_is_best/dataclasses_comparison.py

But included comparisons to:
- msgspec
- SQLModel


# Benchmarks
### Creation Speeds (in ns)

| Rank | Type                        | Time (ns) |
|------|-----------------------------|-----------|
| 0    | tuple                       | 17        |
| 1    | msgspec                     | 45        |
| 2    | dict                        | 53        |
| 3    | dataclass (slots)           | 103       |
| 4    | attr class (slots)          | 104       |
| 5    | plain class (slots)         | 104       |
| 6    | attr class                  | 117       |
| 7    | SimpleNamespace             | 118       |
| 8    | dataclass                   | 120       |
| 9    | plain class                 | 120       |
| 10   | namedtuple                  | 160       |
| 11   | NamedTuple                  | 162       |
| 12   | pydantic                    | 683       |
| 13   | SQLModel (table=False)      | 1769      |
| 14   | SQLAlchemyDataclass         | 2712      |
| 15   | SQLAlchemy                  | 3616      |

### `getattr` Speeds (in ns)

| Rank | Type                        | Time (ns) |
|------|-----------------------------|-----------|
| 0    | tuple                       | 8         |
| 1    | pydantic                    | 8         |
| 2    | dataclass                   | 8         |
| 3    | plain class                 | 8         |
| 4    | plain class (slots)         | 8         |
| 5    | msgspec                     | 8         |
| 6    | attr class (slots)          | 8         |
| 7    | SQLModel (table=False)      | 8         |
| 8    | dataclass (slots)           | 8         |
| 9    | attr class                  | 8         |
| 10   | dict                        | 9         |
| 11   | namedtuple                  | 11        |
| 12   | NamedTuple                  | 11        |
| 13   | SimpleNamespace             | 16        |
| 14   | SQLAlchemyDataclass         | 92        |
| 15   | SQLAlchemy                  | 94        |

### `setattr` Speeds (in ns)

| Rank | Type                        | Time (ns) |
|------|-----------------------------|-----------|
| 0    | dataclass                   | 8         |
| 1    | plain class (slots)         | 8         |
| 2    | dataclass (slots)           | 8         |
| 3    | attr class (slots)          | 8         |
| 4    | plain class                 | 8         |
| 5    | attr class                  | 8         |
| 6    | dict                        | 12        |
| 7    | msgspec                     | 18        |
| 8    | SimpleNamespace             | 19        |
| 9    | SQLAlchemy                  | 337       |
| 10   | SQLAlchemyDataclass         | 346       |
| 11   | pydantic                    | 1233      |
| 12   | SQLModel (table=False)      | 1497      |

### Memory Usage (in bytes)

| Rank | Type                        | Memory Usage (bytes) |
|------|-----------------------------|----------------------|
| 0    | dataclass (slots)           | 160                  |
| 1    | plain class (slots)         | 160                  |
| 2    | msgspec                     | 160                  |
| 3    | tuple                       | 168                  |
| 4    | namedtuple                  | 168                  |
| 5    | NamedTuple                  | 168                  |
| 6    | attr class (slots)          | 176                  |
| 7    | dict                        | 432                  |
| 8    | SimpleNamespace             | 472                  |
| 9    | pydantic                    | 504                  |
| 10   | SQLModel (table=False)      | 504                  |
| 11   | plain class                 | 592                  |
| 12   | dataclass                   | 592                  |
| 13   | attr class                  | 592                  |
