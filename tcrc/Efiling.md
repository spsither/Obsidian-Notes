- When .101 goes down change the permission of storage folder in .60 from
`www-data:efiling` to `www-data:www-data`

### Letter Number race condition
- To solve the race condition, use the register lock to represent who has the current physical register using a Bool in Organization Table
