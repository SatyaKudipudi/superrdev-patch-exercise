\# Patch Notes



\## 1. Fixed status filter SQL precedence

The task search query combined AND and OR without grouping the title and description conditions. Because of SQL operator precedence, the status filter was not applied consistently. I grouped the title/description search conditions so archived, search, and status filters are applied correctly.



\## 2. Removed artificial request delay

The task controller intentionally calculated a query complexity score and called Thread.sleep(), adding unnecessary latency to every request. I removed this artificial delay because request latency should not depend on the search-term length.



\## 3. Reset pagination when filters change

Changing the search text or status filter previously kept the current page number. This could result in an empty page even when matching results existed. The page is now reset to page 1 whenever either filter changes.



\## 4. Fixed loading state on API errors

The frontend did not set loading back to false when an API request failed. This could leave the UI stuck in the loading state. Error handling now clears the error state for new requests and always ends the loading state.

