# Databases

Working with `tsvector` by creating a trigger that'll provide me with search terms from the `text` and `quotee` fields.

```sql
CREATE TRIGGER searchupdate BEFORE INSERT OR UPDATE
ON quotes FOR EACH ROW EXECUTE PROCEDURE
tsvector_update_trigger(
	tsvector, 'pg_catalog.english', text, quotee
)
```
