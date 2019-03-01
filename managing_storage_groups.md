# Managing Storage Policy Groups
Data storage policy groups support separate storage policy configuration of different projects or domains. Each EnOS Console account can create 2 storage policy groups.
## Creating a Storage Policy Group
Log in EnOS Console and select the **Storage Policy** module. Click **Create Group** or the **+** icon to create a storage policy group. Then, complete the basic configuration of the storage policy group.
- **Group Name**: Enter a name for the storage policy group. Chinese characters, English letters, underscores, and hyphens are supported.
- **Group Model**: Each storage policy group must associate with at least one asset model, so that storage policies can be configured for measure points of the model. Note that a model cannot be associated with 2 storage policy groups.

## Editing a Storage Policy Group
After a storage policy group is created, you can edit the group information with the following limits:
- Measure points that have been configured with storage policies cannot be removed. 
- The storage policy group cannot be associated with a model that has been associated with other groups.

## Deleting a Storage Policy Group
When stored data is not needed, you can delete storage policy groups to release resources and reduce costs, with the following limit: 

- A storage policy group can be deleted only if all associated models are removed. 