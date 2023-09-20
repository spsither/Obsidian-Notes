In `openpecha.core.metadata.py`
`PechaMetadata` can be one of the following
- `DiplomaticPechaMetadata` - based on an existing reference
- `OpenPechaMetadata` - for Open Source opf
- `InitialPechaMetadata` - for undecided opf

## issues

line 68 in `core.pecha.py` assumes that `self.meta.source_metadata.items()` exist 
but line 75 in `core.metadata.py` says source_metadata is Optional 

