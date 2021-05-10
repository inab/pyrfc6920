# A library to generate and validate RFC6920 URIs

Naming Things with Hashes [IETF RFC 6920](https://datatracker.ietf.org/doc/html/rfc6920) specifies both `ni` and `nih` schemes, and how they are generated and validated.

This library is composed by methods `generate_ni` (to generate a `ni` URI), `generate_nih` (to generate a `nih` URI) and `validate` (to validate `ni` and `nih` URIs). Both `generate_ni`, `generate_nih` and `validate` understand both file paths and bytearray.

```python
rfc6920.generate_nih(b'Hello World!') 
# It returns 'nih:sha-256;7f83-b165-7ff1-fc53-b92d-c181-48a1-d65d-fc2d-4b1f-a3d6-7728-4add-d200-126d-9069;d'

rfc6920.validate('nih:sha-256;7f83-b165-7ff1-fc53-b92d-c181-48a1-d65d-fc2d-4b1f-a3d6-7728-4add-d200-126d-9069;d', b'Hello World!')
# It returns True

rfc6920.validate('nih:sha-256;7f83-b165-7ff1-fc53-b92d-c181-48a1-d65d-fc2d-4b1f-a3d6-7728-4add-d200-126d-9069;e', b'Hello World!')
# It returns False, wrong check digit

rfc6920.validate('nih:sha-256;7f83-b165-7ff1-fc53-b92d-c181-48a1-d65d-fc2d-4b1f-a3d6-7728-4add-d200-126d-9069;d', b'Hello Mundo!')
# It returns False, different digest
```
