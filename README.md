Simple benchmark for comparing different dataclass-like providers.

Adapted from https://github.com/mCodingLLC/VideosSampleCode/blob/master/videos/079_which_dataclass_is_best/dataclasses_comparison.py

But included comparisons to:
- msgspec
- SQLModel
- SQLAlchemy

Most SQLAlchemy related stuff unfortunately don't quite work.

Sample Benchmark:
creation speeds
0: tuple - 17 ns
1: msgspec - 45 ns
2: dict - 53 ns
3: dataclass (slots) - 103 ns
4: attr class (slots) - 104 ns
5: plain class (slots) - 104 ns
6: attr class - 117 ns
7: SimpleNamespace - 118 ns
8: dataclass - 120 ns
9: plain class - 120 ns
10: namedtuple - 160 ns
11: NamedTuple - 162 ns
12: pydantic - 683 ns
13: SQLModel (table=False) - 1769 ns
14: SQLAlchemyDataclass - 2712 ns
15: SQLAlchemy - 3616 ns

getattr speeds
0: tuple - 8 ns
1: pydantic - 8 ns
2: dataclass - 8 ns
3: plain class - 8 ns
4: plain class (slots) - 8 ns
5: msgspec - 8 ns
6: attr class (slots) - 8 ns
7: SQLModel (table=False) - 8 ns
8: dataclass (slots) - 8 ns
9: attr class - 8 ns
10: dict - 9 ns
11: namedtuple - 11 ns
12: NamedTuple - 11 ns
13: SimpleNamespace - 16 ns
14: SQLAlchemyDataclass - 92 ns
15: SQLAlchemy - 94 ns

setattr speeds
0: dataclass - 8 ns
1: plain class (slots) - 8 ns
2: dataclass (slots) - 8 ns
3: attr class (slots) - 8 ns
4: plain class - 8 ns
5: attr class - 8 ns
6: dict - 12 ns
7: msgspec - 18 ns
8: SimpleNamespace - 19 ns
9: SQLAlchemy - 337 ns
10: SQLAlchemyDataclass - 346 ns
11: pydantic - 1233 ns
12: SQLModel (table=False) - 1497 ns

mem usage
0: dataclass (slots) - 160 bytes
1: plain class (slots) - 160 bytes
2: msgspec - 160 bytes
3: tuple - 168 bytes
4: namedtuple - 168 bytes
5: NamedTuple - 168 bytes
6: attr class (slots) - 176 bytes
7: dict - 432 bytes
8: SimpleNamespace - 472 bytes
9: pydantic - 504 bytes
10: SQLModel (table=False) - 504 bytes
11: plain class - 592 bytes
12: dataclass - 592 bytes
13: attr class - 592 bytes
