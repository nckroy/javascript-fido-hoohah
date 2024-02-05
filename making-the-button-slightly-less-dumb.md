# Making the button slightly less dumb

## Flow

1. User goes to RP with SA button for first time
2. SA says "I have no secrets for you" generate a keypair plz
3. Private key goes into a CHIPS cookie
4. User selects their IdP and the selection is encrypted with priv key
5. Encrypted user IdP sel and pub key are retuned to SA and persisted into Lambda@edge
6. (...time passes...) user comes back to RP, which asks for a pubkey, which is presented to SA and used to dereference the encrypted IdP sel.
7. Encrypted IdP sel is returned to browser and decrypted using SA Javascript using private key stored in CHIPS
8. User's IdP sel is displayed on the magic button

## Result

SA has no way of logging a user's IdP sel across sites.<br>
Sites can't collude because they all have different private keys that each other cannot access because of CHIPS.<br>
User has to pick their IdP the first time they access any RP, but only the first time.<br>
