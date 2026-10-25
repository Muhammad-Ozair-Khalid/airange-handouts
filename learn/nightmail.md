# Field notes: Nightmail

**Packet filters, DNS labels and evidence reconstruction**

## Rebuild a story from DNS questions

DNS names are often used for telemetry, and their labels can carry encoded fragments. A packet capture can contain duplicates, noise, and records observed out of order. Treat every question as a structured record: separate the session identifier, sequence number, data label, and destination suffix before decoding anything.

Filter to DNS queries from the acquisition host. Keep only the collector’s accepted session, map sequence numbers to labels, and collapse exact duplicates. Join labels in sequence order, then decode the documented alphabet and decompress the result. A cryptographic hash gives an independent completeness check; if it does not match, a fragment is missing, duplicated incorrectly, or ordered wrong.

These queries target reserved example domains and the capture is synthetic. Wireshark’s display filters help explore the conversation; a short script is useful for reliable ordering and deduplication.

Learning reference: [Wireshark guide to working with captured packets](https://www.wireshark.org/docs/wsug_html_chunked/ChapterWork.html).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
