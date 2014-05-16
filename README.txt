NOTE:

These tools are becoming obsolete as we move away from using Berkeley DB in
Reddcoin-Qt/reddcoind.

If you are looking for a tool to manipulate the wallet.dat file, you might
want to try https://github.com/jackjack-jj/pywallet

REQUIREMENTS:

You must run Reddcoin-Qt/reddcoind with the "-detachdb" option
or these tools will be unable to read the Berkeley DB files.

----- dbdump.py -----
Run    dbdump.py --help    for usage.  Database files are opened read-only, but
you might want to backup your Reddcoin wallet.dat file just in case.

You must quit Reddcoin before reading the transactions, blocks, or address database files.

Examples:

Print out  wallet keys and transactions:
  dbdump.py --wallet --wallet-tx

Print out the "genesis block" (the very first block in the proof-of-work block chain):
  dbdump.py --block=9f1f5a21034ef45bf096da7a1ede1d9cc2f6d2e80013781969fc01d8acdcb0e2

Print out one of the biggest transactions:
  dbdump.py --transaction=fdbc649fd408241b7da8363aafe3815542344f53408652c885ef33a6cd3d5ff8
  dbdump.py --transaction=fdbc...5ff8

Print out all 'received' transactions that aren't yet spent:
  dbdump.py --wallet-tx-filter='fromMe:False.*spent:False'

Print out all blocks involving transactions to the authors Reddcoin-address:
  dbdump.py --search-blocks=RctBPR4vuQmgDuqABUnrqCWjEDwaqF2FWd

There's a special search term to look for non-standard transactions:
  dbdump.py --search-blocks=NONSTANDARD_CSCRIPTS

----- statistics.py -----
Scan all the transactions in the block chain and dump out a .csv file that shows transaction volume per month.

----- fixwallet.py -----
Half-baked utility that reads a wallet.dat and writes out a new wallet.dat.

Only half-baked because to be really useful I'd have to write serialize routines to re-pack data after modifying it...

----- jsonToCSV.py -----
Read JSON list-of-objects from standard input, writes CSV file to standard output.
Useful for converting reddcoind's listtransactions output to CSV that can be
imported into a spreadsheet.
