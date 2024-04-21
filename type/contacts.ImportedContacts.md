# contacts.ImportedContacts
Object contains info on successfully imported contacts.

```
contacts.importedContacts#77d01c3b imported:Vector<ImportedContact> popular_invites:Vector<PopularContact> retry_contacts:Vector<long> users:Vector<User> = contacts.ImportedContacts;

---functions---

contacts.importContacts#2c800be5 contacts:Vector<InputContact> = contacts.ImportedContacts;
```

## Constructors
| Constructor | Description |
| ---- | ----------- |
| contacts.importedContacts | Info on successfully imported contacts. |


## Methods
| Method | Description |
| ---- | ----------- |
| contacts.importContacts | Imports contacts: saves a full list on the server, adds already registered contacts to the contact list, returns added contacts and their info.Use contacts.addContact to add Telegram contacts without actually using their phone number. |


