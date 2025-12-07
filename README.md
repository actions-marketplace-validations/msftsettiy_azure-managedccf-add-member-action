# Add a member to a CCF network

This action will automate the addition of a member to a CCF network by submitting a proposal and accepting it.

---

## Pre-reqs

The action requires two sets of secrets to be stored in the GitHub repository secrets.

- NEWMEMBERCERT - The certificate of the new member.
- NEWMEMBERKEY - The private key of the new member.

- MEMBERCERT - The certificate that has access to the network, which will be used to sign the transactions for CCF.
- MEMBERKEY - The private key associated with the MEMBERCERT.

---

## Example workflow: Sample

```
on: [push]

jobs:
  ccf-add-member:
    runs-on: ubuntu-latest
    name: Add a member to a CCF network
    env:
      CCF_URL: '<your ccf endpoint>/'
    steps:
      - name: CCF add member
        uses: msftsettiy/azure-managedccf-add-member-action@v0.1.9-alpha
        id: add_member
        env:
          NEWMEMBERCERTD: ${{ secrets.NEWMEMBERCERT }}
          NEWMEMBERKEYD: ${{ secrets.NEWMEMBERKEY }}
          CERTD: ${{ secrets.MEMBERCERT }}
          KEYD: ${{ secrets.MEMBERKEY }}
```
