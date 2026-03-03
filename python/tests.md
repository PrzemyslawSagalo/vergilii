# Tests

## Test Naming Conventions - pytest

A test suite is only as maintainable as it is readable. You should set up a clear naming convention at the beginning of your project and stick to it to ensure test discovery works predictably and accurately reflects business requirements.

* **Fixtures are Nouns, Not Verbs**
    Fixtures represent state, data, or resources injected into a test. Name them as the object they represent (`pre_existing_array_uri`, `db_connection`), never as the procedural steps taken to construct them (`create_pre_existing_array`, `setup_database`).

* **Protect the Discovery Namespace**
    Test runners rely on lexical matching for test discovery. Applying a test prefix (e.g., `test_`) to fixtures or helper utilities pollutes the namespace and causes runner warnings. Use `sample_pandas_df` instead of `test_pandas_df`.

* **Behavioral Descriptions**
    Test classes must use PascalCase and begin with `Test` (e.g., `TestIngestPandas`). Test methods must use snake_case and begin with `test_` (e.g., `test_ingest_to_new_array`). The name should clearly convey the action and the expected outcome.
