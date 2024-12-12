---
title: Unlocking XOR Cipher with Python
date: 2019-10-17 14:24:00 +0000
categories: [Projects, Code]
tags: [Projects]     # TAG names should always be lowercase
math: true
---

**Abstract:** This work focuses on breaking the XOR cipher, an encryption method that employs a key consisting of a block of text. The plaintext is divided into blocks of the same size as the key, with each block encrypted using the XOR operation. Decryption is accomplished by applying the XOR operation again to the encrypted blocks. In this study, we aim to recover the key used in the encryption of a specific message, given only the size of the key.

The encrypted text is:
>f4c4e842d8d77c7323770fa3520a954bd385e859c085d726267c4c9a4148885196e6fa45cdc0f17f677700ea50438a4ad9d7bb47ccc0bd3e26669fea410aa95fc448fa16f0d7f431266002af1b0a974bc6caf551d685ec26223209a6005a9651d5c0e85999c0ee27a63209a4004f881ec4c0f843dcd7f93c677609ea54458051c585e216c8d0f873297d4cb9450a8a5bd5c0e85fcdc4f3732a7315a5524f971ed3ddeb5ad0c6fc302e7d02af530a9751d4d7fe16d4ccbd2322601fa54e4bca1ef7d0f547ccc0bd3d2e3209a6004e8d5fd4c9f416cac4ff3667631923004f971edacabb47ccc0bd3b263208af0058815dd9d7ff57cb85f132677509a4544fc81ed8ccbb46d6d7bd2232fb42ea6544c44cd3c4f75fddc4f97f676105af4d5a965b96cdfe16c9c0f320267603ea515f811ed8cabb5ed8dcbd3e227f03b8494bc45dd9c9fe55cdcceb326b3200a5005b915b96d4ee5fc344bd2022734cbf4e4bc458d9d7f65799c1f87323770aaf4e59851ed2c0bb5ad885f82037770fa3450a8c4bdbc4f5579785d13267741eab534fc41cc2caff5999d1f4362a6203ea504b975fd2cabb50ccc0bd3e227803b8020a8a5196ccf552d0c6fc73366709ea4144905bc585e843dac0f93a22600da400478150d9d6bb55d6d6fc20677f0da64159c81ec5ccf55999d4e836673f0aaf4c439e53d3cbef539485f132677509a4544fc452d7d6bb53dacdfc73227c4caf4c0a8b52c0ccff599785d936347609ea4c5f8159d989bb45dcc8f839267c18af004c965fc5c0bb58d685e93a227c09ea564b8857d2c0e116cccbf42522601fab4c11c447d989bb46d6d7bd362d7701ba4c45c81edbc0bb55d8d7fc3033771ea35a45c44ed9d7bb44dcc6f22123731eea50588158d3d7fe58cdc0f036296609ea4c45971edec0f85ed6d6bd3e267e03b90053c81ed7d6761a99c6fc202e321ca54458095f96c1fe55d0d7bd2232774ce85445805196d1f253d4d5f27337731fab4445c458c3c0bb46dccaef716b321fa300448b1ed0d0fe44d885ed3c356319af004f881ec6d7fe45dccbe936677f09ea504b965bd5c0bb42d8cbbd3b28601ea34246811ed5caf65999c0f17337731fab4445df1ec4c0f843dcd7f93c67660da4544b971ed5c4f757d4ccf93223771fe6005e8550c2cae816cbcaee27357d1fea43c78a57d5cae816c085fe21327700af5306c44ad7cbef57ca85f0322b731fea41498757d9cbfe459585ec26223200ab00478153d9d7f25799c0ee7337731eab0047091ed5caf65999c9fc73337701af5245975f96c9ee4c99d4e836677300bf4d48965f96d0f516ca56ef372e7603ea4d5f975bd985ff5399c9fc7331771eaddc4f8a44d78bbb97fad07c3d33731fea564f875bc585f35399d4e836237308a5004b9452d7d6ef57ddcabd3732600da4544fc456d9d7fa459585f83d676702ea52438a5d45cbbb59cac6e821283208af4c0a905fdac9fe449585f93634621923530a805b96c9fe53cb85e83d263202a554438757d785fe5899c9fc7334770fa949d98a1ec6caf75fdaccfc3f66323caf5245c452d785ed53cbc1fc3767771fea515f811ed8cabb45d0c0f02335774ca64f0a89dfc585ed53cbc2f23d3d7d1fa5004e811edac4bb44d8dffc732f6701ab4e4bc45fc6c4e953dac0bd322b7e81f10042854dc2c4bb55d0c0ef2728321cbf4e5e8b1296c9f44599c6ef3a2a7b02ab4c4f971ec5caf516dec0f3272232012b530a8857dbd5f2579585f0b2343205a44f4c8150c5cced578285f82033734cab46439653d7c6f2c5d785f33c677e0dea484b835196d5f444c8d0f8733e7d4ca74959895196cdfa4fd885f032337308a5004bc44bd885e853cb85f5262a7302a51a0a814d96d0f55799cdf23d226118ab0053c44ec4cafd43d7c1fc73247d02bc4949875745cbb51606f0f3732e7c08a35643804bd985fe4599d5f821297b0fa34f598b0196f5ee53ca85ee36677e03ea4c43954bdfc1fa16c085ee3667730fab42d9ca1ef3d6f416dcd6bd3f28321dbf450a9d5196c9f757d4cabd2629734ca8554f8a5f96c4f855d056f37d674205af4e59815096c6eed7d7d1f273377703b8004f971ec6c4e95799c9fc73347d0fa3454e855a96d4ee5399c0ee36677b02ae495c8d5ac3cabb45d0c2fc7323771fbe49468550d2cabb45cc85eb36297702a50053c44fc3c0bb53d785eb363d3208af004f8857dbccf557cbc9f27334774cbb5543814cd785f859d7d1ef32356009b9544b961ec5d0bb57dac6f4a029321eaf435f964cdfc0f552d685fc73267c9fa449478b4d9a85f657d5c0f93a247702a9494bc44796caef44d8d6bd31267809b04159c44dd3c8fe5cd8cbe936343c4c8f4e0a885196d4ee5399c4bd3eaa321faf00588158dfc0e9539585f936257d4ca94f44825bc5c4e916c8d0f873267a03b8410a885fdbc0f542d685f33c677a0da84558c45fc6d7f440dcc6f532237d4ca745408b4c96c0f716cdccf83e377d4cae450a895796c9f254dcd7e932233e4ca6495b9157d2c4f552d685fc73347705b90045c44ddfc0ef5399d1f42328614cbb554fc45dd9cbf44cdacab373166709ea4546c453c3cbff5999c0ee732f7d1eb84948885b9a85fe4599d0f332676409b8444b801ec7d0fe16d7cabd3d227109b9495e851ed2c0f659cad1ef32247b9fa40e0aa65fc5d1fa4454c4bd26293204af43428b1ec6c4e95799d5ef3c25731ea64f06c45bd885ef59ddcabd30266103f0004f8a1ec3cbbb55d8c8ed3c677609ea43458a5dd3cbef44d8c6f4a0293219a4004f9c1ec6ccfa58d0d6e932676109ea515f81544585ff5399cdfc3e256009ea590a8150c2caf555dcd6bd3f283203a84c43835fc4caf516d885fe3c2a771eb9450a9150d785e957cdc4b17337771ea5005c8d48d78bbb78d685f820677609ea45598b1296d6f25899c0f03126600ba50c0a805b96c9f416c8d0f873366705af5245c456d7c7f757cb85fc3b28600df10053851ed2cce9df99c87c20677308af4c4b8a4ad389bb45d085f5323e3203a941598dcdd889bb57d5c2f2732af31fea5345864cd385fe45cdc0bd32346702be4f0a805b96c9fa16cbc4e932697d24a3547cb14c

We only know that the key is a 32-digit hexadecimal, so we will figure out how to decrypt it.


```python
mensaje='f4c4e842d8d77c7323770fa3520a954bd385e859c085d726267c4c9a4148885196e6fa45cdc0f17f677700ea50438a4ad9d7bb47ccc0bd3e26669fea410aa95fc448fa16f0d7f431266002af1b0a974bc6caf551d685ec26223209a6005a9651d5c0e85999c0ee27a63209a4004f881ec4c0f843dcd7f93c677609ea54458051c585e216c8d0f873297d4cb9450a8a5bd5c0e85fcdc4f3732a7315a5524f971ed3ddeb5ad0c6fc302e7d02af530a9751d4d7fe16d4ccbd2322601fa54e4bca1ef7d0f547ccc0bd3d2e3209a6004e8d5fd4c9f416cac4ff3667631923004f971edacabb47ccc0bd3b263208af0058815dd9d7ff57cb85f132677509a4544fc81ed8ccbb46d6d7bd2232fb42ea6544c44cd3c4f75fddc4f97f676105af4d5a965b96cdfe16c9c0f320267603ea515f811ed8cabb5ed8dcbd3e227f03b8494bc45dd9c9fe55cdcceb326b3200a5005b915b96d4ee5fc344bd2022734cbf4e4bc458d9d7f65799c1f87323770aaf4e59851ed2c0bb5ad885f82037770fa3450a8c4bdbc4f5579785d13267741eab534fc41cc2caff5999d1f4362a6203ea504b975fd2cabb50ccc0bd3e227803b8020a8a5196ccf552d0c6fc73366709ea4144905bc585e843dac0f93a22600da400478150d9d6bb55d6d6fc20677f0da64159c81ec5ccf55999d4e836673f0aaf4c439e53d3cbef539485f132677509a4544fc452d7d6bb53dacdfc73227c4caf4c0a8b52c0ccff599785d936347609ea4c5f8159d989bb45dcc8f839267c18af004c965fc5c0bb58d685e93a227c09ea564b8857d2c0e116cccbf42522601fab4c11c447d989bb46d6d7bd362d7701ba4c45c81edbc0bb55d8d7fc3033771ea35a45c44ed9d7bb44dcc6f22123731eea50588158d3d7fe58cdc0f036296609ea4c45971edec0f85ed6d6bd3e267e03b90053c81ed7d6761a99c6fc202e321ca54458095f96c1fe55d0d7bd2232774ce85445805196d1f253d4d5f27337731fab4445c458c3c0bb46dccaef716b321fa300448b1ed0d0fe44d885ed3c356319af004f881ec6d7fe45dccbe936677f09ea504b965bd5c0bb42d8cbbd3b28601ea34246811ed5caf65999c0f17337731fab4445df1ec4c0f843dcd7f93c67660da4544b971ed5c4f757d4ccf93223771fe6005e8550c2cae816cbcaee27357d1fea43c78a57d5cae816c085fe21327700af5306c44ad7cbef57ca85f0322b731fea41498757d9cbfe459585ec26223200ab00478153d9d7f25799c0ee7337731eab0047091ed5caf65999c9fc73337701af5245975f96c9ee4c99d4e836677300bf4d48965f96d0f516ca56ef372e7603ea4d5f975bd985ff5399c9fc7331771eaddc4f8a44d78bbb97fad07c3d33731fea564f875bc585f35399d4e836237308a5004b9452d7d6ef57ddcabd3732600da4544fc456d9d7fa459585f83d676702ea52438a5d45cbbb59cac6e821283208af4c0a905fdac9fe449585f93634621923530a805b96c9fe53cb85e83d263202a554438757d785fe5899c9fc7334770fa949d98a1ec6caf75fdaccfc3f66323caf5245c452d785ed53cbc1fc3767771fea515f811ed8cabb45d0c0f02335774ca64f0a89dfc585ed53cbc2f23d3d7d1fa5004e811edac4bb44d8dffc732f6701ab4e4bc45fc6c4e953dac0bd322b7e81f10042854dc2c4bb55d0c0ef2728321cbf4e5e8b1296c9f44599c6ef3a2a7b02ab4c4f971ec5caf516dec0f3272232012b530a8857dbd5f2579585f0b2343205a44f4c8150c5cced578285f82033734cab46439653d7c6f2c5d785f33c677e0dea484b835196d5f444c8d0f8733e7d4ca74959895196cdfa4fd885f032337308a5004bc44bd885e853cb85f5262a7302a51a0a814d96d0f55799cdf23d226118ab0053c44ec4cafd43d7c1fc73247d02bc4949875745cbb51606f0f3732e7c08a35643804bd985fe4599d5f821297b0fa34f598b0196f5ee53ca85ee36677e03ea4c43954bdfc1fa16c085ee3667730fab42d9ca1ef3d6f416dcd6bd3f28321dbf450a9d5196c9f757d4cabd2629734ca8554f8a5f96c4f855d056f37d674205af4e59815096c6eed7d7d1f273377703b8004f971ec6c4e95799c9fc73347d0fa3454e855a96d4ee5399c0ee36677b02ae495c8d5ac3cabb45d0c2fc7323771fbe49468550d2cabb45cc85eb36297702a50053c44fc3c0bb53d785eb363d3208af004f8857dbccf557cbc9f27334774cbb5543814cd785f859d7d1ef32356009b9544b961ec5d0bb57dac6f4a029321eaf435f964cdfc0f552d685fc73267c9fa449478b4d9a85f657d5c0f93a247702a9494bc44796caef44d8d6bd31267809b04159c44dd3c8fe5cd8cbe936343c4c8f4e0a885196d4ee5399c4bd3eaa321faf00588158dfc0e9539585f936257d4ca94f44825bc5c4e916c8d0f873267a03b8410a885fdbc0f542d685f33c677a0da84558c45fc6d7f440dcc6f532237d4ca745408b4c96c0f716cdccf83e377d4cae450a895796c9f254dcd7e932233e4ca6495b9157d2c4f552d685fc73347705b90045c44ddfc0ef5399d1f42328614cbb554fc45dd9cbf44cdacab373166709ea4546c453c3cbff5999c0ee732f7d1eb84948885b9a85fe4599d0f332676409b8444b801ec7d0fe16d7cabd3d227109b9495e851ed2c0f659cad1ef32247b9fa40e0aa65fc5d1fa4454c4bd26293204af43428b1ec6c4e95799d5ef3c25731ea64f06c45bd885ef59ddcabd30266103f0004f8a1ec3cbbb55d8c8ed3c677609ea43458a5dd3cbef44d8c6f4a0293219a4004f9c1ec6ccfa58d0d6e932676109ea515f81544585ff5399cdfc3e256009ea590a8150c2caf555dcd6bd3f283203a84c43835fc4caf516d885fe3c2a771eb9450a9150d785e957cdc4b17337771ea5005c8d48d78bbb78d685f820677609ea45598b1296d6f25899c0f03126600ba50c0a805b96c9f416c8d0f873366705af5245c456d7c7f757cb85fc3b28600df10053851ed2cce9df99c87c20677308af4c4b8a4ad389bb45d085f5323e3203a941598dcdd889bb57d5c2f2732af31fea5345864cd385fe45cdc0bd32346702be4f0a805b96c9fa16cbc4e932697d24a3547cb14c'
k=len(mensaje)
print("The number of characters in the encrypted message is:\n"+str(k))
```

    The number of characters in the encrypted message is:
    4448


We will proceed to XOR the first 128-bit block with the others.


```python
n=len(mensaje)
bloque1=mensaje[0:32]
lista=[]
for i in range(1,139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(bloque1,16)^int(bloque,16)
    bloque=hex(bloque)
    lista.append(bloque)
    print(bloque)


```

    0x2741001b1852ab55050b433913421d1a
    0x6222120715178d0c44000f4902491f01
    0x2d1353051417c14d0511904913003c14
    0x308c12542800884205170d0c49000200
    0x320e1d130e529055014506055250031a
    0x2104001b411792548545060752451d55
    0x300410010400854f44010649064f151a
    0x31410a54100784000a0a431a17001f10
    0x2104001d15138f0009041a0600450255
    0x27190318081180430d0a0d0c0100021a
    0x201316540c1bc150011710061c415f55
    0x3141d051417c14e0d45060552441814
    0x200d1c54121383454414168052450255
    0x2e0e53051417c1480545070c52521416
    0x2d13171513528d414402060706455d55
    0x2c0853040e00c151118c4d49374e5107
    0x27001f1d0513850c44160a0c1f500310
    0x6209165411178f5305010c4903551455
    0x2c0e531c000bc14d01080c1b1b415116
    0x2d0d1617151b974148450f0652510410
    0x6210061d1b93c1530104431c1c415113
    0x2d131e15411684000000050c1c531055
    0x26045318005284531400000017001900
    0x2f001d154f52ad414403110801455157
    0x360e171b4106884509150c4902410214
    0x260e53121417c14d010f0c1b50001f1a
    0x62081d100811800015100649134e0510
    0x314100010217854901170207524d141b
    0x2d1253170e0180534408020513535d55
    0x31081d1b410394454448050c1e490b18
    0x270f07114c528d414402060706455119
    0x23125311021a8000010b430c1e001e19
    0x3408171b4f52a545170106491e551412
    0x2d4d5307041f844a050b170c52460314
    0x3104531a0e529549010b064904411d1c
    0x26040954141c8856011710081e1b510c
    0x2d4d53040e00c1450e000e191e4f5d55
    0x2f0453170000804310001100084f5105
    0x2d13530604118e520004114902521413
    0x2713161a15178c450a1106491e4f0255
    0x2a04101c0e01c14d05090c1a52595d55
    0x23129e58411180530d45130616529c14
    0x620516170800c1511100434b064f151a
    0x62151a110c028e0014041008164f5113
    0x37045304041d930248451000524e1e55
    0x241416060052914f1614160c52451d55
    0x32131607041c95454408064902410310
    0x21045300001cc1480b171100104c1455
    0x210e1e1b41178d0014041008164f4a55
    0x300410010400854f4411020706410255
    0x21001f150c1b8541000010455254101b
    0x360e0054131d9254160a104911cd1f1c
    0x210e00541852825211000f0c010c5101
    0x230f071512528c41080410491343121c
    0x2d0f16074d52905501450f08524d1418
    0x2d131a154117920014041108524d9c55
    0x210e1e1b411e800010000e0c004f0214
    0x620d060e4103944544040f1c1f420314
    0x62141d54128193440d010c491f550210
    0x2d411711411e80001200110e8e451f0f
    0x234f53d52207004e1004104904451210
    0x31411b11410394450004070652410119
    0x23120715051dc144111702070645511d
    0x2d1312074d52844e44100d4900491f16
    0xb10f531b121194520b45070c1e000514
    0x2e0d16064d5285451715168001001510
    0x620d16111352944e05450d060649121c
    0x2341161a411e80001700000a1bd31f55
    0x320e1f1d021b804c4545330c004f5119
    0x23410511131680444400104903551455
    0x2c0e530708178c50160043051d001c94
    0x3141051113158e4e1e0a100652441455
    0x2e005306000880000c100e081c415114
    0x320001110217c14108098e5252481006
    0x36005317081793540b45131c1c541e59
    0x620d1c0741119349090c0d081e450255
    0x310e1d5406178f5401450e8801001d1c
    0x2f111a154d528cc117450a071d46141b
    0x310805155a5284531004430814490318
    0x23021a870f528f4f440902491a41161a
    0x62111c06100784001d0a43041b531c1a
    0x6209120d00528c411004070652415100
    0x2c4100111352895509040d0648001406
    0x62141d15411a8e4e0116170852595105
    0x300e15010f168000070a0d1f1b43121c
    0xb10f5d54de278f000d0b070004491500
    0x2d411607410284520a0c00001d531e4a
    0x623106111252924544090c491e490000
    0x2b051254185292454404000810d35f55
    0x7121c540401c14c0b45121c1700081a
    0x620d1f150c1dc1550a04430b07451f14
    0x6200101708818f0e44350a0c1c53141b
    0x620206950f068e0014000c1b52450255
    0x32000115411e8000170a000017441011
    0x6210061141179245440c0d0d1b561811
    0x370e5307081580000000101d1b4c101b
    0x260e5307145297450a000d0652595104
    0x370453110f5297451e45070c52451d1c
    0x2f081d15131e8e001700431807491407
    0x2341101b0f0693411617061a06410355
    0x31145315021188d30a45110c11550307
    0x2b041d100e528000050b90071b4d1e06
    0x6e411e150d17854907000d0a1b41510c
    0x620e07060001c142050f061313535106
    0x270c161e001c9545174b432c1c001d1a
    0x621006114113c14d8945100c52521413
    0x2b0401114d528545060a430a1d4e1710
    0x3100015410078400050d0c1b13001d14
    0x2f041d000e528f4f440d020b17525114
    0x32131c0204118941000a4304174a1e07
    0x62041f54151b844d140a430d17001c1c
    0x620d1a1604009541004943051b51041c
    0x26001d100e52800017000a1a524f5106
    0x2b040711410688500b16431807455116
    0x2d0f1c0e021dcf0035100649174c5118
    0x370f171b411792000c0a111b1b421d10
    0x6e41160741078f414413061b16411555
    0x331416540f1dc14e0106061a1b541055
    0x26041e1b12069341070c90075c003314
    0x311512068c13c1550a450b0c11481e55
    0x320001154102934f060411051d0c5110
    0x2c41071b051dc14305160c5352451f55
    0x370f5317001f914f44010649114f1f16
    0x270f0706001188d30a45160752450955
    0x3208121a08019541441606490355141f
    0xb1411711411a804d061706490b00141b
    0x360e1d170401c14c0b450c0b1e491614
    0x300e1d540052824f0900111a1700041b
    0x234101151513cd001400110652561803
    0x234f533a0e5284534401064917531e59
    0x62121a1a41178c42051704065e001510
    0x620d1c541007840015100a0c004f511d
    0x23031f15135280480b17025252591055
    0x2608019d411f00534404070c1e411f01
    0x274d5307085289411d450c0a13531886
    0x2c4d53150d158e0009841049014f1307
    0x274116071517c14117100d1d1d001510
    0x620d1254131395414a0a2b0006762407


By analyzing the ASCII code, we have the following:

If we XOR non-special characters (a, b, c, d, ..., z) with a space " ", we get their respective uppercase letters (A, B, C, ..., D), that is, characters between 41 and 5A in hexadecimal.

If we XOR non-special characters (a, b, c, d, ..., z) with accented vowels (á, é, í, ó, ú) or ñ, we get characters in the form of 8x and 9x in hexadecimal.

If we XOR non-special characters (a, b, c, d, ..., z) with accented uppercase vowels (Á, É, Í, Ó, Ú) or Ñ, we get characters in the form of ax and bx in hexadecimal.

If we XOR non-special characters (a, b, c, d, ..., z) with uppercase letters (A, B, C, ..., Z), we get characters in the form of 2x and 3x in hexadecimal, and also, for the same words, we would get a space " " or 20 in hexadecimal.


```python
#CASO ESPACIO ' '
alfa=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
n=len(alfa)
Char2=' '
for i in range(n):
    Char1=alfa[i]
    char1=Char1.encode("latin-1").hex()
    char2=Char2.encode("latin-1").hex()
    result=int(char1,16)^int(char2,16)
    result=str(hex(result))
    #result=bytes.fromhex(result).decode('latin-1')
    print(Char1+' xor '+Char2+' = '+result)
```

    a xor   = 0x41
    b xor   = 0x42
    c xor   = 0x43
    d xor   = 0x44
    e xor   = 0x45
    f xor   = 0x46
    g xor   = 0x47
    h xor   = 0x48
    i xor   = 0x49
    j xor   = 0x4a
    k xor   = 0x4b
    l xor   = 0x4c
    m xor   = 0x4d
    n xor   = 0x4e
    o xor   = 0x4f
    p xor   = 0x50
    q xor   = 0x51
    r xor   = 0x52
    s xor   = 0x53
    t xor   = 0x54
    u xor   = 0x55
    v xor   = 0x56
    w xor   = 0x57
    x xor   = 0x58
    y xor   = 0x59
    z xor   = 0x5a



```python
#CASO tilde minúscula
alfa=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
tilde=['á','é','í','ó','ú']
for j in range(len(tilde)):
    n=len(alfa)
    print(tilde[j])
    Char2=tilde[j]
    for i in range(n):
        Char1=alfa[i]
        char1=Char1.encode("latin-1").hex()
        char2=Char2.encode("latin-1").hex()
        result=int(char1,16)^int(char2,16)
        result=str(hex(result))
        #result=bytes.fromhex(result).decode('latin-1')
        print(Char1+' xor '+Char2+' = '+result)
```

    á
    a xor á = 0x80
    b xor á = 0x83
    c xor á = 0x82
    d xor á = 0x85
    e xor á = 0x84
    f xor á = 0x87
    g xor á = 0x86
    h xor á = 0x89
    i xor á = 0x88
    j xor á = 0x8b
    k xor á = 0x8a
    l xor á = 0x8d
    m xor á = 0x8c
    n xor á = 0x8f
    o xor á = 0x8e
    p xor á = 0x91
    q xor á = 0x90
    r xor á = 0x93
    s xor á = 0x92
    t xor á = 0x95
    u xor á = 0x94
    v xor á = 0x97
    w xor á = 0x96
    x xor á = 0x99
    y xor á = 0x98
    z xor á = 0x9b
    é
    a xor é = 0x88
    b xor é = 0x8b
    c xor é = 0x8a
    d xor é = 0x8d
    e xor é = 0x8c
    f xor é = 0x8f
    g xor é = 0x8e
    h xor é = 0x81
    i xor é = 0x80
    j xor é = 0x83
    k xor é = 0x82
    l xor é = 0x85
    m xor é = 0x84
    n xor é = 0x87
    o xor é = 0x86
    p xor é = 0x99
    q xor é = 0x98
    r xor é = 0x9b
    s xor é = 0x9a
    t xor é = 0x9d
    u xor é = 0x9c
    v xor é = 0x9f
    w xor é = 0x9e
    x xor é = 0x91
    y xor é = 0x90
    z xor é = 0x93
    í
    a xor í = 0x8c
    b xor í = 0x8f
    c xor í = 0x8e
    d xor í = 0x89
    e xor í = 0x88
    f xor í = 0x8b
    g xor í = 0x8a
    h xor í = 0x85
    i xor í = 0x84
    j xor í = 0x87
    k xor í = 0x86
    l xor í = 0x81
    m xor í = 0x80
    n xor í = 0x83
    o xor í = 0x82
    p xor í = 0x9d
    q xor í = 0x9c
    r xor í = 0x9f
    s xor í = 0x9e
    t xor í = 0x99
    u xor í = 0x98
    v xor í = 0x9b
    w xor í = 0x9a
    x xor í = 0x95
    y xor í = 0x94
    z xor í = 0x97
    ó
    a xor ó = 0x92
    b xor ó = 0x91
    c xor ó = 0x90
    d xor ó = 0x97
    e xor ó = 0x96
    f xor ó = 0x95
    g xor ó = 0x94
    h xor ó = 0x9b
    i xor ó = 0x9a
    j xor ó = 0x99
    k xor ó = 0x98
    l xor ó = 0x9f
    m xor ó = 0x9e
    n xor ó = 0x9d
    o xor ó = 0x9c
    p xor ó = 0x83
    q xor ó = 0x82
    r xor ó = 0x81
    s xor ó = 0x80
    t xor ó = 0x87
    u xor ó = 0x86
    v xor ó = 0x85
    w xor ó = 0x84
    x xor ó = 0x8b
    y xor ó = 0x8a
    z xor ó = 0x89
    ú
    a xor ú = 0x9b
    b xor ú = 0x98
    c xor ú = 0x99
    d xor ú = 0x9e
    e xor ú = 0x9f
    f xor ú = 0x9c
    g xor ú = 0x9d
    h xor ú = 0x92
    i xor ú = 0x93
    j xor ú = 0x90
    k xor ú = 0x91
    l xor ú = 0x96
    m xor ú = 0x97
    n xor ú = 0x94
    o xor ú = 0x95
    p xor ú = 0x8a
    q xor ú = 0x8b
    r xor ú = 0x88
    s xor ú = 0x89
    t xor ú = 0x8e
    u xor ú = 0x8f
    v xor ú = 0x8c
    w xor ú = 0x8d
    x xor ú = 0x82
    y xor ú = 0x83
    z xor ú = 0x80



```python
#CASO tilde mayúscula
alfa=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
tilde=['Á','É','Í','Ó','Ú']
for j in range(len(tilde)):
    n=len(alfa)
    print(tilde[j])
    Char2=tilde[j]
    for i in range(n):
        Char1=alfa[i]
        char1=Char1.encode("latin-1").hex()
        char2=Char2.encode("latin-1").hex()
        result=int(char1,16)^int(char2,16)
        result=str(hex(result))
        #result=bytes.fromhex(result).decode('latin-1')
        print(Char1+' xor '+Char2+' = '+result)
```

    Á
    a xor Á = 0xa0
    b xor Á = 0xa3
    c xor Á = 0xa2
    d xor Á = 0xa5
    e xor Á = 0xa4
    f xor Á = 0xa7
    g xor Á = 0xa6
    h xor Á = 0xa9
    i xor Á = 0xa8
    j xor Á = 0xab
    k xor Á = 0xaa
    l xor Á = 0xad
    m xor Á = 0xac
    n xor Á = 0xaf
    o xor Á = 0xae
    p xor Á = 0xb1
    q xor Á = 0xb0
    r xor Á = 0xb3
    s xor Á = 0xb2
    t xor Á = 0xb5
    u xor Á = 0xb4
    v xor Á = 0xb7
    w xor Á = 0xb6
    x xor Á = 0xb9
    y xor Á = 0xb8
    z xor Á = 0xbb
    É
    a xor É = 0xa8
    b xor É = 0xab
    c xor É = 0xaa
    d xor É = 0xad
    e xor É = 0xac
    f xor É = 0xaf
    g xor É = 0xae
    h xor É = 0xa1
    i xor É = 0xa0
    j xor É = 0xa3
    k xor É = 0xa2
    l xor É = 0xa5
    m xor É = 0xa4
    n xor É = 0xa7
    o xor É = 0xa6
    p xor É = 0xb9
    q xor É = 0xb8
    r xor É = 0xbb
    s xor É = 0xba
    t xor É = 0xbd
    u xor É = 0xbc
    v xor É = 0xbf
    w xor É = 0xbe
    x xor É = 0xb1
    y xor É = 0xb0
    z xor É = 0xb3
    Í
    a xor Í = 0xac
    b xor Í = 0xaf
    c xor Í = 0xae
    d xor Í = 0xa9
    e xor Í = 0xa8
    f xor Í = 0xab
    g xor Í = 0xaa
    h xor Í = 0xa5
    i xor Í = 0xa4
    j xor Í = 0xa7
    k xor Í = 0xa6
    l xor Í = 0xa1
    m xor Í = 0xa0
    n xor Í = 0xa3
    o xor Í = 0xa2
    p xor Í = 0xbd
    q xor Í = 0xbc
    r xor Í = 0xbf
    s xor Í = 0xbe
    t xor Í = 0xb9
    u xor Í = 0xb8
    v xor Í = 0xbb
    w xor Í = 0xba
    x xor Í = 0xb5
    y xor Í = 0xb4
    z xor Í = 0xb7
    Ó
    a xor Ó = 0xb2
    b xor Ó = 0xb1
    c xor Ó = 0xb0
    d xor Ó = 0xb7
    e xor Ó = 0xb6
    f xor Ó = 0xb5
    g xor Ó = 0xb4
    h xor Ó = 0xbb
    i xor Ó = 0xba
    j xor Ó = 0xb9
    k xor Ó = 0xb8
    l xor Ó = 0xbf
    m xor Ó = 0xbe
    n xor Ó = 0xbd
    o xor Ó = 0xbc
    p xor Ó = 0xa3
    q xor Ó = 0xa2
    r xor Ó = 0xa1
    s xor Ó = 0xa0
    t xor Ó = 0xa7
    u xor Ó = 0xa6
    v xor Ó = 0xa5
    w xor Ó = 0xa4
    x xor Ó = 0xab
    y xor Ó = 0xaa
    z xor Ó = 0xa9
    Ú
    a xor Ú = 0xbb
    b xor Ú = 0xb8
    c xor Ú = 0xb9
    d xor Ú = 0xbe
    e xor Ú = 0xbf
    f xor Ú = 0xbc
    g xor Ú = 0xbd
    h xor Ú = 0xb2
    i xor Ú = 0xb3
    j xor Ú = 0xb0
    k xor Ú = 0xb1
    l xor Ú = 0xb6
    m xor Ú = 0xb7
    n xor Ú = 0xb4
    o xor Ú = 0xb5
    p xor Ú = 0xaa
    q xor Ú = 0xab
    r xor Ú = 0xa8
    s xor Ú = 0xa9
    t xor Ú = 0xae
    u xor Ú = 0xaf
    v xor Ú = 0xac
    w xor Ú = 0xad
    x xor Ú = 0xa2
    y xor Ú = 0xa3
    z xor Ú = 0xa0



```python
#CASO alfabeto mayuscula
alfa=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
ALFA=['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']
for j in range(len(ALFA)):
    n=len(alfa)
    print(ALFA[j])
    Char2=ALFA[j]
    for i in range(n):
        Char1=alfa[i]
        char1=Char1.encode("latin-1").hex()
        char2=Char2.encode("latin-1").hex()
        result=int(char1,16)^int(char2,16)
        result=str(hex(result))
        #result=bytes.fromhex(result).decode('latin-1')
        print(Char1+' xor '+Char2+' = '+result)
```

    A
    a xor A = 0x20
    b xor A = 0x23
    c xor A = 0x22
    d xor A = 0x25
    e xor A = 0x24
    f xor A = 0x27
    g xor A = 0x26
    h xor A = 0x29
    i xor A = 0x28
    j xor A = 0x2b
    k xor A = 0x2a
    l xor A = 0x2d
    m xor A = 0x2c
    n xor A = 0x2f
    o xor A = 0x2e
    p xor A = 0x31
    q xor A = 0x30
    r xor A = 0x33
    s xor A = 0x32
    t xor A = 0x35
    u xor A = 0x34
    v xor A = 0x37
    w xor A = 0x36
    x xor A = 0x39
    y xor A = 0x38
    z xor A = 0x3b
    B
    a xor B = 0x23
    b xor B = 0x20
    c xor B = 0x21
    d xor B = 0x26
    e xor B = 0x27
    f xor B = 0x24
    g xor B = 0x25
    h xor B = 0x2a
    i xor B = 0x2b
    j xor B = 0x28
    k xor B = 0x29
    l xor B = 0x2e
    m xor B = 0x2f
    n xor B = 0x2c
    o xor B = 0x2d
    p xor B = 0x32
    q xor B = 0x33
    r xor B = 0x30
    s xor B = 0x31
    t xor B = 0x36
    u xor B = 0x37
    v xor B = 0x34
    w xor B = 0x35
    x xor B = 0x3a
    y xor B = 0x3b
    z xor B = 0x38
    C
    a xor C = 0x22
    b xor C = 0x21
    c xor C = 0x20
    d xor C = 0x27
    e xor C = 0x26
    f xor C = 0x25
    g xor C = 0x24
    h xor C = 0x2b
    i xor C = 0x2a
    j xor C = 0x29
    k xor C = 0x28
    l xor C = 0x2f
    m xor C = 0x2e
    n xor C = 0x2d
    o xor C = 0x2c
    p xor C = 0x33
    q xor C = 0x32
    r xor C = 0x31
    s xor C = 0x30
    t xor C = 0x37
    u xor C = 0x36
    v xor C = 0x35
    w xor C = 0x34
    x xor C = 0x3b
    y xor C = 0x3a
    z xor C = 0x39
    D
    a xor D = 0x25
    b xor D = 0x26
    c xor D = 0x27
    d xor D = 0x20
    e xor D = 0x21
    f xor D = 0x22
    g xor D = 0x23
    h xor D = 0x2c
    i xor D = 0x2d
    j xor D = 0x2e
    k xor D = 0x2f
    l xor D = 0x28
    m xor D = 0x29
    n xor D = 0x2a
    o xor D = 0x2b
    p xor D = 0x34
    q xor D = 0x35
    r xor D = 0x36
    s xor D = 0x37
    t xor D = 0x30
    u xor D = 0x31
    v xor D = 0x32
    w xor D = 0x33
    x xor D = 0x3c
    y xor D = 0x3d
    z xor D = 0x3e
    E
    a xor E = 0x24
    b xor E = 0x27
    c xor E = 0x26
    d xor E = 0x21
    e xor E = 0x20
    f xor E = 0x23
    g xor E = 0x22
    h xor E = 0x2d
    i xor E = 0x2c
    j xor E = 0x2f
    k xor E = 0x2e
    l xor E = 0x29
    m xor E = 0x28
    n xor E = 0x2b
    o xor E = 0x2a
    p xor E = 0x35
    q xor E = 0x34
    r xor E = 0x37
    s xor E = 0x36
    t xor E = 0x31
    u xor E = 0x30
    v xor E = 0x33
    w xor E = 0x32
    x xor E = 0x3d
    y xor E = 0x3c
    z xor E = 0x3f
    F
    a xor F = 0x27
    b xor F = 0x24
    c xor F = 0x25
    d xor F = 0x22
    e xor F = 0x23
    f xor F = 0x20
    g xor F = 0x21
    h xor F = 0x2e
    i xor F = 0x2f
    j xor F = 0x2c
    k xor F = 0x2d
    l xor F = 0x2a
    m xor F = 0x2b
    n xor F = 0x28
    o xor F = 0x29
    p xor F = 0x36
    q xor F = 0x37
    r xor F = 0x34
    s xor F = 0x35
    t xor F = 0x32
    u xor F = 0x33
    v xor F = 0x30
    w xor F = 0x31
    x xor F = 0x3e
    y xor F = 0x3f
    z xor F = 0x3c
    G
    a xor G = 0x26
    b xor G = 0x25
    c xor G = 0x24
    d xor G = 0x23
    e xor G = 0x22
    f xor G = 0x21
    g xor G = 0x20
    h xor G = 0x2f
    i xor G = 0x2e
    j xor G = 0x2d
    k xor G = 0x2c
    l xor G = 0x2b
    m xor G = 0x2a
    n xor G = 0x29
    o xor G = 0x28
    p xor G = 0x37
    q xor G = 0x36
    r xor G = 0x35
    s xor G = 0x34
    t xor G = 0x33
    u xor G = 0x32
    v xor G = 0x31
    w xor G = 0x30
    x xor G = 0x3f
    y xor G = 0x3e
    z xor G = 0x3d
    H
    a xor H = 0x29
    b xor H = 0x2a
    c xor H = 0x2b
    d xor H = 0x2c
    e xor H = 0x2d
    f xor H = 0x2e
    g xor H = 0x2f
    h xor H = 0x20
    i xor H = 0x21
    j xor H = 0x22
    k xor H = 0x23
    l xor H = 0x24
    m xor H = 0x25
    n xor H = 0x26
    o xor H = 0x27
    p xor H = 0x38
    q xor H = 0x39
    r xor H = 0x3a
    s xor H = 0x3b
    t xor H = 0x3c
    u xor H = 0x3d
    v xor H = 0x3e
    w xor H = 0x3f
    x xor H = 0x30
    y xor H = 0x31
    z xor H = 0x32
    I
    a xor I = 0x28
    b xor I = 0x2b
    c xor I = 0x2a
    d xor I = 0x2d
    e xor I = 0x2c
    f xor I = 0x2f
    g xor I = 0x2e
    h xor I = 0x21
    i xor I = 0x20
    j xor I = 0x23
    k xor I = 0x22
    l xor I = 0x25
    m xor I = 0x24
    n xor I = 0x27
    o xor I = 0x26
    p xor I = 0x39
    q xor I = 0x38
    r xor I = 0x3b
    s xor I = 0x3a
    t xor I = 0x3d
    u xor I = 0x3c
    v xor I = 0x3f
    w xor I = 0x3e
    x xor I = 0x31
    y xor I = 0x30
    z xor I = 0x33
    J
    a xor J = 0x2b
    b xor J = 0x28
    c xor J = 0x29
    d xor J = 0x2e
    e xor J = 0x2f
    f xor J = 0x2c
    g xor J = 0x2d
    h xor J = 0x22
    i xor J = 0x23
    j xor J = 0x20
    k xor J = 0x21
    l xor J = 0x26
    m xor J = 0x27
    n xor J = 0x24
    o xor J = 0x25
    p xor J = 0x3a
    q xor J = 0x3b
    r xor J = 0x38
    s xor J = 0x39
    t xor J = 0x3e
    u xor J = 0x3f
    v xor J = 0x3c
    w xor J = 0x3d
    x xor J = 0x32
    y xor J = 0x33
    z xor J = 0x30
    K
    a xor K = 0x2a
    b xor K = 0x29
    c xor K = 0x28
    d xor K = 0x2f
    e xor K = 0x2e
    f xor K = 0x2d
    g xor K = 0x2c
    h xor K = 0x23
    i xor K = 0x22
    j xor K = 0x21
    k xor K = 0x20
    l xor K = 0x27
    m xor K = 0x26
    n xor K = 0x25
    o xor K = 0x24
    p xor K = 0x3b
    q xor K = 0x3a
    r xor K = 0x39
    s xor K = 0x38
    t xor K = 0x3f
    u xor K = 0x3e
    v xor K = 0x3d
    w xor K = 0x3c
    x xor K = 0x33
    y xor K = 0x32
    z xor K = 0x31
    L
    a xor L = 0x2d
    b xor L = 0x2e
    c xor L = 0x2f
    d xor L = 0x28
    e xor L = 0x29
    f xor L = 0x2a
    g xor L = 0x2b
    h xor L = 0x24
    i xor L = 0x25
    j xor L = 0x26
    k xor L = 0x27
    l xor L = 0x20
    m xor L = 0x21
    n xor L = 0x22
    o xor L = 0x23
    p xor L = 0x3c
    q xor L = 0x3d
    r xor L = 0x3e
    s xor L = 0x3f
    t xor L = 0x38
    u xor L = 0x39
    v xor L = 0x3a
    w xor L = 0x3b
    x xor L = 0x34
    y xor L = 0x35
    z xor L = 0x36
    M
    a xor M = 0x2c
    b xor M = 0x2f
    c xor M = 0x2e
    d xor M = 0x29
    e xor M = 0x28
    f xor M = 0x2b
    g xor M = 0x2a
    h xor M = 0x25
    i xor M = 0x24
    j xor M = 0x27
    k xor M = 0x26
    l xor M = 0x21
    m xor M = 0x20
    n xor M = 0x23
    o xor M = 0x22
    p xor M = 0x3d
    q xor M = 0x3c
    r xor M = 0x3f
    s xor M = 0x3e
    t xor M = 0x39
    u xor M = 0x38
    v xor M = 0x3b
    w xor M = 0x3a
    x xor M = 0x35
    y xor M = 0x34
    z xor M = 0x37
    N
    a xor N = 0x2f
    b xor N = 0x2c
    c xor N = 0x2d
    d xor N = 0x2a
    e xor N = 0x2b
    f xor N = 0x28
    g xor N = 0x29
    h xor N = 0x26
    i xor N = 0x27
    j xor N = 0x24
    k xor N = 0x25
    l xor N = 0x22
    m xor N = 0x23
    n xor N = 0x20
    o xor N = 0x21
    p xor N = 0x3e
    q xor N = 0x3f
    r xor N = 0x3c
    s xor N = 0x3d
    t xor N = 0x3a
    u xor N = 0x3b
    v xor N = 0x38
    w xor N = 0x39
    x xor N = 0x36
    y xor N = 0x37
    z xor N = 0x34
    O
    a xor O = 0x2e
    b xor O = 0x2d
    c xor O = 0x2c
    d xor O = 0x2b
    e xor O = 0x2a
    f xor O = 0x29
    g xor O = 0x28
    h xor O = 0x27
    i xor O = 0x26
    j xor O = 0x25
    k xor O = 0x24
    l xor O = 0x23
    m xor O = 0x22
    n xor O = 0x21
    o xor O = 0x20
    p xor O = 0x3f
    q xor O = 0x3e
    r xor O = 0x3d
    s xor O = 0x3c
    t xor O = 0x3b
    u xor O = 0x3a
    v xor O = 0x39
    w xor O = 0x38
    x xor O = 0x37
    y xor O = 0x36
    z xor O = 0x35
    P
    a xor P = 0x31
    b xor P = 0x32
    c xor P = 0x33
    d xor P = 0x34
    e xor P = 0x35
    f xor P = 0x36
    g xor P = 0x37
    h xor P = 0x38
    i xor P = 0x39
    j xor P = 0x3a
    k xor P = 0x3b
    l xor P = 0x3c
    m xor P = 0x3d
    n xor P = 0x3e
    o xor P = 0x3f
    p xor P = 0x20
    q xor P = 0x21
    r xor P = 0x22
    s xor P = 0x23
    t xor P = 0x24
    u xor P = 0x25
    v xor P = 0x26
    w xor P = 0x27
    x xor P = 0x28
    y xor P = 0x29
    z xor P = 0x2a
    Q
    a xor Q = 0x30
    b xor Q = 0x33
    c xor Q = 0x32
    d xor Q = 0x35
    e xor Q = 0x34
    f xor Q = 0x37
    g xor Q = 0x36
    h xor Q = 0x39
    i xor Q = 0x38
    j xor Q = 0x3b
    k xor Q = 0x3a
    l xor Q = 0x3d
    m xor Q = 0x3c
    n xor Q = 0x3f
    o xor Q = 0x3e
    p xor Q = 0x21
    q xor Q = 0x20
    r xor Q = 0x23
    s xor Q = 0x22
    t xor Q = 0x25
    u xor Q = 0x24
    v xor Q = 0x27
    w xor Q = 0x26
    x xor Q = 0x29
    y xor Q = 0x28
    z xor Q = 0x2b
    R
    a xor R = 0x33
    b xor R = 0x30
    c xor R = 0x31
    d xor R = 0x36
    e xor R = 0x37
    f xor R = 0x34
    g xor R = 0x35
    h xor R = 0x3a
    i xor R = 0x3b
    j xor R = 0x38
    k xor R = 0x39
    l xor R = 0x3e
    m xor R = 0x3f
    n xor R = 0x3c
    o xor R = 0x3d
    p xor R = 0x22
    q xor R = 0x23
    r xor R = 0x20
    s xor R = 0x21
    t xor R = 0x26
    u xor R = 0x27
    v xor R = 0x24
    w xor R = 0x25
    x xor R = 0x2a
    y xor R = 0x2b
    z xor R = 0x28
    S
    a xor S = 0x32
    b xor S = 0x31
    c xor S = 0x30
    d xor S = 0x37
    e xor S = 0x36
    f xor S = 0x35
    g xor S = 0x34
    h xor S = 0x3b
    i xor S = 0x3a
    j xor S = 0x39
    k xor S = 0x38
    l xor S = 0x3f
    m xor S = 0x3e
    n xor S = 0x3d
    o xor S = 0x3c
    p xor S = 0x23
    q xor S = 0x22
    r xor S = 0x21
    s xor S = 0x20
    t xor S = 0x27
    u xor S = 0x26
    v xor S = 0x25
    w xor S = 0x24
    x xor S = 0x2b
    y xor S = 0x2a
    z xor S = 0x29
    T
    a xor T = 0x35
    b xor T = 0x36
    c xor T = 0x37
    d xor T = 0x30
    e xor T = 0x31
    f xor T = 0x32
    g xor T = 0x33
    h xor T = 0x3c
    i xor T = 0x3d
    j xor T = 0x3e
    k xor T = 0x3f
    l xor T = 0x38
    m xor T = 0x39
    n xor T = 0x3a
    o xor T = 0x3b
    p xor T = 0x24
    q xor T = 0x25
    r xor T = 0x26
    s xor T = 0x27
    t xor T = 0x20
    u xor T = 0x21
    v xor T = 0x22
    w xor T = 0x23
    x xor T = 0x2c
    y xor T = 0x2d
    z xor T = 0x2e
    U
    a xor U = 0x34
    b xor U = 0x37
    c xor U = 0x36
    d xor U = 0x31
    e xor U = 0x30
    f xor U = 0x33
    g xor U = 0x32
    h xor U = 0x3d
    i xor U = 0x3c
    j xor U = 0x3f
    k xor U = 0x3e
    l xor U = 0x39
    m xor U = 0x38
    n xor U = 0x3b
    o xor U = 0x3a
    p xor U = 0x25
    q xor U = 0x24
    r xor U = 0x27
    s xor U = 0x26
    t xor U = 0x21
    u xor U = 0x20
    v xor U = 0x23
    w xor U = 0x22
    x xor U = 0x2d
    y xor U = 0x2c
    z xor U = 0x2f
    V
    a xor V = 0x37
    b xor V = 0x34
    c xor V = 0x35
    d xor V = 0x32
    e xor V = 0x33
    f xor V = 0x30
    g xor V = 0x31
    h xor V = 0x3e
    i xor V = 0x3f
    j xor V = 0x3c
    k xor V = 0x3d
    l xor V = 0x3a
    m xor V = 0x3b
    n xor V = 0x38
    o xor V = 0x39
    p xor V = 0x26
    q xor V = 0x27
    r xor V = 0x24
    s xor V = 0x25
    t xor V = 0x22
    u xor V = 0x23
    v xor V = 0x20
    w xor V = 0x21
    x xor V = 0x2e
    y xor V = 0x2f
    z xor V = 0x2c
    W
    a xor W = 0x36
    b xor W = 0x35
    c xor W = 0x34
    d xor W = 0x33
    e xor W = 0x32
    f xor W = 0x31
    g xor W = 0x30
    h xor W = 0x3f
    i xor W = 0x3e
    j xor W = 0x3d
    k xor W = 0x3c
    l xor W = 0x3b
    m xor W = 0x3a
    n xor W = 0x39
    o xor W = 0x38
    p xor W = 0x27
    q xor W = 0x26
    r xor W = 0x25
    s xor W = 0x24
    t xor W = 0x23
    u xor W = 0x22
    v xor W = 0x21
    w xor W = 0x20
    x xor W = 0x2f
    y xor W = 0x2e
    z xor W = 0x2d
    X
    a xor X = 0x39
    b xor X = 0x3a
    c xor X = 0x3b
    d xor X = 0x3c
    e xor X = 0x3d
    f xor X = 0x3e
    g xor X = 0x3f
    h xor X = 0x30
    i xor X = 0x31
    j xor X = 0x32
    k xor X = 0x33
    l xor X = 0x34
    m xor X = 0x35
    n xor X = 0x36
    o xor X = 0x37
    p xor X = 0x28
    q xor X = 0x29
    r xor X = 0x2a
    s xor X = 0x2b
    t xor X = 0x2c
    u xor X = 0x2d
    v xor X = 0x2e
    w xor X = 0x2f
    x xor X = 0x20
    y xor X = 0x21
    z xor X = 0x22
    Y
    a xor Y = 0x38
    b xor Y = 0x3b
    c xor Y = 0x3a
    d xor Y = 0x3d
    e xor Y = 0x3c
    f xor Y = 0x3f
    g xor Y = 0x3e
    h xor Y = 0x31
    i xor Y = 0x30
    j xor Y = 0x33
    k xor Y = 0x32
    l xor Y = 0x35
    m xor Y = 0x34
    n xor Y = 0x37
    o xor Y = 0x36
    p xor Y = 0x29
    q xor Y = 0x28
    r xor Y = 0x2b
    s xor Y = 0x2a
    t xor Y = 0x2d
    u xor Y = 0x2c
    v xor Y = 0x2f
    w xor Y = 0x2e
    x xor Y = 0x21
    y xor Y = 0x20
    z xor Y = 0x23
    Z
    a xor Z = 0x3b
    b xor Z = 0x38
    c xor Z = 0x39
    d xor Z = 0x3e
    e xor Z = 0x3f
    f xor Z = 0x3c
    g xor Z = 0x3d
    h xor Z = 0x32
    i xor Z = 0x33
    j xor Z = 0x30
    k xor Z = 0x31
    l xor Z = 0x36
    m xor Z = 0x37
    n xor Z = 0x34
    o xor Z = 0x35
    p xor Z = 0x2a
    q xor Z = 0x2b
    r xor Z = 0x28
    s xor Z = 0x29
    t xor Z = 0x2e
    u xor Z = 0x2f
    v xor Z = 0x2c
    w xor Z = 0x2d
    x xor Z = 0x22
    y xor Z = 0x23
    z xor Z = 0x20



```python
#CASO Ñ
alfa=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
n=len(alfa)
Char2='Ñ'
for i in range(n):
    Char1=alfa[i]
    char1=Char1.encode("latin-1").hex()
    char2=Char2.encode("latin-1").hex()
    result=int(char1,16)^int(char2,16)
    result=str(hex(result))
    #result=bytes.fromhex(result).decode('latin-1')
    print(Char1+' xor '+Char2+' = '+result)
```

    a xor Ñ = 0xb0
    b xor Ñ = 0xb3
    c xor Ñ = 0xb2
    d xor Ñ = 0xb5
    e xor Ñ = 0xb4
    f xor Ñ = 0xb7
    g xor Ñ = 0xb6
    h xor Ñ = 0xb9
    i xor Ñ = 0xb8
    j xor Ñ = 0xbb
    k xor Ñ = 0xba
    l xor Ñ = 0xbd
    m xor Ñ = 0xbc
    n xor Ñ = 0xbf
    o xor Ñ = 0xbe
    p xor Ñ = 0xa1
    q xor Ñ = 0xa0
    r xor Ñ = 0xa3
    s xor Ñ = 0xa2
    t xor Ñ = 0xa5
    u xor Ñ = 0xa4
    v xor Ñ = 0xa7
    w xor Ñ = 0xa6
    x xor Ñ = 0xa9
    y xor Ñ = 0xa8
    z xor Ñ = 0xab



```python
#CASO ñ
alfa=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
n=len(alfa)
Char2='ñ'
for i in range(n):
    Char1=alfa[i]
    char1=Char1.encode("latin-1").hex()
    char2=Char2.encode("latin-1").hex()
    result=int(char1,16)^int(char2,16)
    result=str(hex(result))
    #result=bytes.fromhex(result).decode('latin-1')
    print(Char1+' xor '+Char2+' = '+result)
```

    a xor ñ = 0x90
    b xor ñ = 0x93
    c xor ñ = 0x92
    d xor ñ = 0x95
    e xor ñ = 0x94
    f xor ñ = 0x97
    g xor ñ = 0x96
    h xor ñ = 0x99
    i xor ñ = 0x98
    j xor ñ = 0x9b
    k xor ñ = 0x9a
    l xor ñ = 0x9d
    m xor ñ = 0x9c
    n xor ñ = 0x9f
    o xor ñ = 0x9e
    p xor ñ = 0x81
    q xor ñ = 0x80
    r xor ñ = 0x83
    s xor ñ = 0x82
    t xor ñ = 0x85
    u xor ñ = 0x84
    v xor ñ = 0x87
    w xor ñ = 0x86
    x xor ñ = 0x89
    y xor ñ = 0x88
    z xor ñ = 0x8b


-----------------------

Thus, for the first block of 'lista', we have 0x2741001b1852ab55050b433913421d1a, which tells us that the XOR between the second byte of block 1 and block 2 gives 41, so there must be a space. After analyzing the space case, we conclude that the only way to get 41 is by XORing 'a' and ' ', so 'a' must be in one of the plaintext blocks in the second byte. We will create a program to help us assemble the key.


```python
bloque1=mensaje[0:32]
bloque2=mensaje[32:64]
aproach="00"+"a".encode("latin-1").hex()+"0"*28
result1=int(bloque1,16)^int(aproach,16)
result1=hex(result1)
result1="0x"+"00"+result1[4:6]+"0"*28
result2=int(bloque2,16)^int(aproach,16)
result2=hex(result2)
result2="0x"+"00"+result2[4:6]+"0"*28
print("For block 1, part of the key could be: " + result1 + "\nFor block 2, part of the key could be: " + result2)

```

    For block 1, part of the key could be: 0x00a50000000000000000000000000000
    For block 2, part of the key could be: 0x00e40000000000000000000000000000


We will now proceed to look for inconsistencies. First, let's assume that 0x00e40000000000000000000000000000 is part of the key.


```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="00e40000000000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque=bloque[4:6]
    bloque=bytes.fromhex(bloque).decode('latin-1')
    print(bloque)
```


    a
    
    3
    ¬
    .
    $
    $
    a
    $
    9
    3
    4
    -
    .
    3
    (

    )
    .
    -
    0
    3
    $

    .
    .
    (
    a
    2
    (
    /
    2
    (
    m
    $
    $
    m
    $
    3
    3
    $
    2
    %
    5
    $
    4
    3
    $
    .
    $

    .
    .
    /
    /
    3
    .
    -
    4
    a
    o
    a
    2
    3
    /
    -
    -
    a
    .
    a
    .
    a



    -
    .
    1
    (
    "
    1
    )
    a
    4
    .
    /
    a
    
    %
    2
    -

    "

    0
    .
    .
    $
    (
    a
    4
    $
    a
    .
    ,
    0
    $

    $
    3
    $
    -

    $
    /
    /
    a
    4
    $
    5

    a
    /
    /
    (
    a
    .
    .
    a
    o
    2
    -
    #
    (
    m
    m
    a
    -


Concluímos que 0x00e40000000000000000000000000000 no podrá ser una llave.


```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="00a50000000000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque=bloque[4:6]
    bloque=bytes.fromhex(bloque).decode('latin-1')
    print(bloque)
```

    a

    C
    r
    í
    o
    e
    e

    e
    x
    r
    u
    l
    o
    r
    i
    a
    h
    o
    l
    q
    r
    e
    a
    o
    o
    i

    s
    i
    n
    s
    i
    ,
    e
    e
    ,
    e
    r
    r
    e
    s
    d
    t
    e
    u
    r
    e
    o
    e
    a
    o
    o
    n
    n
    r
    o
    l
    u

    .

    s
    r
    n
    l
    l

    o

    o

    a
    a
    a
    l
    o
    p
    i
    c
    p
    h

    u
    o
    n

    P
    d
    s
    l
    a
    c
    a
    q
    o
    o
    e
    i

    u
    e

    o
    m
    q
    e
    a
    e
    r
    e
    l
    a
    e
    n
    n

    u
    e
    t
    a

    n
    n
    i

    o
    o

    .
    s
    l
    b
    i
    ,
    ,

    l


Note that with 0x00a50000000000000000000000000000, we get a better result.


```python
lista[2]
```




    '0x2d1353051417c14d0511904913003c14'



Note that, from the previous program (with which we concluded that 0x00a50000000000000000000000000000 is part of the key), we determined that in block 3 or in block 1, there must be a 'C'. This necessarily implies that in block 3 or block 1, the first byte must be a space. I will proceed to create a program that shows what happens in both cases.


```python
bloque1=mensaje[0:32]
bloque3=mensaje[64:96]
aproach=" ".encode("latin-1").hex()+"0"*30
result1=int(bloque1,16)^int(aproach,16)
result1=hex(result1)
result1="0x"+result1[2:4]+"a5"+"0"*28

result3=int(bloque3,16)^int(aproach,16)
result3=hex(result3)
result3="0x"+result3[2:4]+"a5"+"0"*28
print("For block 1, part of the key could be: " + result1 + "\nFor block 3, part of the key could be: " + result3)
```

    For block 1, part of the key could be: 0xd4a50000000000000000000000000000
    For block 3, part of the key could be: 0xb6a50000000000000000000000000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="b6a50000000000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:4]
    bloque2=bloque[4:6]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Ba
    e
     C
    or
    rí
    po
    ce
    re
    s
    ce
    ex
    br
    Au
    bl
    lo
    or
    ni
    ea
     h
    no
    ol
     q
    or
    de
    ma
    to
    do
     i
    s
    os
    si
    en
    as
    vi
    o,
    se
    de
    o,
    me
    or
    er
    he
    as
     d
     t
    ue
    fu
    pr
    ce
    co
    re
    ca
    to
    co
    an
    on
    or
    co
     l
     u
    o
    a.
    s
    as
    or
    ón
    ll
     l
    a
    po
    a
    no
    s
    la
    pa
    ta
     l
    so
    mp
    si
    ac
     p
     h
    n
     u
    ro
    ón
    o
     P
    id
    Es
     l
     a
     c
    pa
     q
    uo
    do
    ue
    mi
    a
    su
    ie
    ,
     o
    em
     q
    ie
    sa
    me
    pr
     e
     l
    da
    ie
    on
    un
    ,
    qu
    de
    st
    pa
    n
    un
    en
    pi
    ó
    to
    ro
    a
    a.
     s
     l
    ab
    di
    e,
    n,
    e
     l


Note that in block 62 there is an 'a.' Therefore, the next character must be a space, reasoning as we have already reasoned:


```python
bloque1=mensaje[0:32]
bloque62=mensaje[32*(62-1):32*62]
aproach="0"*4+" ".encode("latin-1").hex()+"0"*26

result1=int(bloque1,16)^int(aproach,16)
result1=hex(result1)
result1="0xb6a5"+result1[6:8]+"0"*26

result2=int(bloque62,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a5"+result2[6:8]+"0"*26
print("For block 1, part of the key could be: " + result1 + "\nFor block 62, part of the key could be: " + result2)
```

    For block 1, part of the key could be: 0xb6a5c800000000000000000000000000
    For block 62, part of the key could be: 0xb6a59b00000000000000000000000000


Nuevamente procedemos por casos:


```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b00000000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:6]
    bloque2=bloque[6:8]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bas
    e s
     Ca
    or
    ría
    pon
    ces
    rec
    s y
    ces
    exp
    bre
    Aun
    blo
    lo
    ord
    ni
    eal
     he
    no
    ole
     qu
    orm
    de
    man
    tod
    do
     in
    s s
    os
    sin
    ent
    as
    vid
    o,
    se
    dez
    o,
    me
    or
    ere
    hec
    así
     de
     ti
    ue
    fue
    pre
    ce
    com
    rec
    cal
    tos
    cos
    ant
    one
    ori
    com
     lu
     un
    o d
    a.
    s h
    ast
    ora
    ón
    lle
     le
    a e
    pol
    a v
    no
    s v
    la
    par
    ta
     lo
    son
    mpi
    siv
    aci
     po
     ha
    n s
     un
    rof
    ón.
    o e
     Pu
    ida
    Eso
     ll
     ac
     cu
    par
     qu
    uo
    do
    ue
    min
    a c
    su
    ien
    , m
     ot
    eme
     qu
    ier
    sar
    men
    pro
     el
     li
    dan
    iet
    ono
    und
    , e
    que
    dem
    sta
    par
    n t
    un
    ent
    pia
    ó d
    ton
    ron
    a r
    a.
     si
     lo
    abl
    dir
    e,
    n,
    e e
     la


Note that in block 87 there is an 'ón.'. Therefore, the next character must be a space, reasoning as we have already reasoned:


```python
bloque1=mensaje[0:32]
bloque87=mensaje[32*(87-1):32*87]
aproach="0"*6+" ".encode("latin-1").hex()+"0"*24

result1=int(bloque1,16)^int(aproach,16)
result1=hex(result1)
result1="0xb6a59b"+result1[8:10]+"0"*24

result2=int(bloque87,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b"+result2[8:10]+"0"*24
print("For block 1, part of the key could be: " + result1 + "\nFor block 87, part of the key could be: " + result2)
```

    For block 1, part of the key could be: 0xb6a59b62000000000000000000000000
    For block 87, part of the key could be: 0xb6a59b36000000000000000000000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b62000000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:8]
    bloque2=bloque[8:10]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bas
    e s;
     Ca'
    or %
    ríat
    pon3
    ces;
    rec!
    s yt
    ces=
    exp8
    bret
    Aun%
    blot
    lo %
    ord5
    ni $
    eal=
     het
    no <
    ole7
     qu=
    orm5
    de 8
    man5
    tod;
    do 2
     in0
    s s!
    os 7
    sin;
    ent1
    as 1
    vid;
    o, '
    se :
    dezt
    o, $
    me 7
    or &
    ere:
    hec<
    asíx
     de7
     ti1
    ue $
    fue&
    pre'
    ce  
    com;
    rec!
    cal5
    tost
    cost
    ant5
    one'
    ori5
    com;
     lu.
     unt
    o d1
    a. õ
    s h1
    ast5
    ora'
    ón ;
    lle&
     le1
    a e:
    pol=
    a v1
    no '
    s v1
    la &
    par1
    ta 7
     lo'
    sont
    mpi5
    siv5
    aci§
     po&
     ha-
    n s1
     un5
    rof!
    ón.t
    o e'
     Pu1
    idat
    Esot
     ll5
     ac7
     cuµ
    par5
     qu1
    uo '
    do '
    ue 1
    min5
    a c;
    su 5
    ien0
    , m5
     ot&
    eme>
     qu1
    ier1
    sart
    men
    pro"
     elt
     li6
    dan0
    iet1
    ono.
    und;
    , e'
    quet
    dem;
    sta&
    par5
    n t;
    un 7
    ent&
    pia:
    ó d1
    ton7
    ront
    a r5
    a. 
     si:
     lot
    abl5
    dir½
    e, '
    n, 5
    e e'
     lat


We conclude that this key possibility cannot be, let's look at the other one.


```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36000000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:8]
    bloque2=bloque[8:10]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bast
    e so
     Cas
    or q
    ría
    pong
    ceso
    recu
    s y
    cesi
    expl
    bre
    Aunq
    blo
    lo q
    orda
    ni p
    eali
     he
    no h
    olec
     qui
    orma
    de l
    mana
    todo
    do f
     ind
    s su
    os c
    sino
    ente
    as e
    vido
    o, s
    se n
    dez
    o, p
    me c
    or r
    eren
    hech
    así,
     dec
     tie
    ue p
    fuer
    pres
    ce t
    como
    recu
    cala
    tos
    cos
    anta
    ones
    oria
    como
     luz
     un
    o de
    a. ¡
    s he
    asta
    oras
    ón o
    ller
     lee
    a en
    poli
    a ve
    no s
    s ve
    la r
    pare
    ta c
     los
    son
    mpia
    siva
    ació
     por
     hay
    n se
     una
    rofu
    ón.
    o es
     Pue
    ida
    Eso
     lla
     acc
     cuá
    para
     que
    uo s
    do s
    ue e
    mina
    a co
    su a
    iend
    , ma
     otr
    emej
     que
    iere
    sar
    ment
    prov
     el
     lib
    dand
    iete
    onoz
    undo
    , es
    que
    demo
    star
    para
    n to
    un c
    entr
    pian
    ó de
    tonc
    ron
    a ra
    a. N
     sin
     lo
    abla
    diré
    e, s
    n, a
    e es
     la


Note that in block 1 it says 'Bast'; we conclude that it must end in 'a', proceeding in a similar manner:


```python
bloque1=mensaje[0:32]
aproach="0"*8+"a".encode("latin-1").hex()+"0"*22

result2=int(bloque1,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b36"+result2[10:12]+"0"*22
print("Our key would be completed with: " + result2)
```

    Our key would be completed with: 0xb6a59b36b90000000000000000000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36b90000000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:10]
    bloque2=bloque[10:12]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Basta
    e soy
     Cast
    or qu
    ría I
    pongo
    ceso
    recue
    s y q
    cesit
    expli
    bre m
    Aunqu
    blo s
    lo qu
    ordar
    ni po
    ealid
     he p
    no ha
    olect
     quiz
    orma
    de la
    mana.
    todo
    do fu
     indi
    s suc
    os co
    sino
    ente-
    as ec
    vido.
    o, se
    se no
    dez u
    o, po
    me ca
    or re
    erent
    hecho
    así,
     deci
     tiem
    ue pe
    fuera
    prese
    ce ta
    como
    recue
    calam
    tos r
    cos y
    antas
    ones,
    oria
    como
     luz
     un s
    o de
    a. ¡C
    s he
    astad
    oras,
    ón os
    ller,
     leer
    a en
    polic
    a ver
    no si
    s ver
    la ra
    parec
    ta ci
     los
    son g
    mpia,
    siva;
    ación
     porq
     haya
    n ser
     una
    rofun
    ón. ¿
    o es
     Pues
    ida y
    Eso e
     llam
     acci
     cuán
    para
     que
    uo si
    do su
    ue en
    minar
    a con
    su ac
    iendo
    , mal
     otra
    emeja
     que
    iere,
    sar q
    mento
    prove
     el t
     libe
    dando
    iete
    onozc
    undo
    , es
    que n
    demos
    starí
    para
    n tod
    un ca
    entra
    piani
    ó de
    tonce
    ron a
    a rat
    a. No
     sin
     lo q
    ablar
    diré
    e, si
    n, al
    e est
     la r


Note that in block 18 it says 'ealid'; we conclude that it must end in 'ad', proceeding in a similar manner:


```python
bloque18=mensaje[32*(18-1):32*18]
aproach="0"*10+"ad".encode("latin-1").hex()+"0"*18

result2=int(bloque18,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b36b9"+result2[12:16]+"0"*18
print("Our key would be completed with: " + result2)
```

    Our key would be completed with: 0xb6a59b36b9a59d000000000000000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36b9a59d000000000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:12]
    bloque2=bloque[12:16]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bastará
    e soy J
     Castel
    or que
    ría Iri
    pongo q
    ceso es
    recuerd
    s y que
    cesitan
    explica
    bre mi
    Aunque
    blo sab
    lo que
    ordar l
    ni por
    ealidad
     he pen
    no hay
    olectiv
     quizá
    orma de
    de la e
    mana. L
    todo ti
    do fue
     indica
    s suced
    os cosa
    sino qu
    ente- l
    as echa
    vido. D
    o, seme
    se no t
    dez uni
    o, por
    me cara
    or reco
    erentem
    hechos
    así, ca
     decir
     tiempo
    ue peor
    fuera p
    present
    ce tan
    como el
    recuerd
    calamid
    tos ros
    cos y c
    antas m
    ones, q
    oria es
    como la
     luz qu
     un sór
    o de la
    a. ¡Cuá
    s he qu
    astado
    oras, e
    ón oscu
    ller, d
     leer u
    a en la
    policia
    a verda
    no siem
    s vergo
    la raza
    parece
    ta cier
     los cr
    son gen
    mpia, m
    siva; e
    ación n
     porque
     haya m
    n ser h
     una ho
    rofunda
    ón. ¿Un
    o es pe
     Pues s
    ida y s
    Eso es
     llamo
     acción
     cuánto
    para la
     que es
    uo siga
    do su v
    ue en v
    minarlo
    a contr
    su acci
    iendo a
    , maled
     otras
    emejant
     que a
    iere, d
    sar que
    mento n
    provech
     el tie
     libert
    dando a
    iete ti
    onozco.
    undo es
    , es un
    que no
    demostr
    staría
    para pr
    n todo
    un camp
    entraci
    pianist
    ó de ha
    tonces
    ron a c
    a rata,
    a. No e
     sin em
     lo que
    ablar a
    diré má
    e, si h
    n, algo
    e este
     la rat


In line 6, we have 'pongo q'; we conclude that it must end in 'ue':


```python
bloque6=mensaje[32*(6-1):32*6]
aproach="0"*14+"ue".encode("latin-1").hex()+"0"*14

result2=int(bloque6,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b36b9a59d"+result2[16:20]+"0"*14
print("Our key would be completed with: " + result2)
```

    Our key would be completed with: 0xb6a59b36b9a59d534700000000000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36b9a59d534700000000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:16]
    bloque2=bloque[16:20]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bastará d
    e soy Jua
     Castel,
    or que ma
    ría Iriba
    pongo que
    ceso está
    recuerdo
    s y que n
    cesitan m
    explicaci
    bre mi pe
    Aunque ni
    blo sabe
    lo que ha
    ordar la
    ni por qu
    ealidad,
     he pensa
    no hay me
    olectiva,
     quizá se
    orma de d
    de la esp
    mana. La
    todo tiem
    do fue me
     indica q
    s sucedie
    os cosas
    sino que
    ente- la
    as echa e
    vido. Des
    o, semeja
    se no tie
    dez unive
    o, por ej
    me caract
    or record
    erentemen
    hechos ma
    así, casi
     decir qu
     tiempo p
    ue peor",
    fuera por
    presente
    ce tan ho
    como el p
    recuerdo
    calamidad
    tos rostr
    cos y cru
    antas mal
    ones, que
    oria es p
    como la t
     luz que
     un sórdi
    o de la v
    a. ¡Cuánt
    s he qued
    astado du
    oras, en
    ón oscuro
    ller, des
     leer una
    a en la s
    policial!
    a verdad
    no siempr
    s vergonz
    la raza h
    parece al
    ta cierto
     los crim
    son gente
    mpia, más
    siva; est
    ación no
     porque y
     haya mat
    n ser hum
     una hone
    rofunda c
    ón. ¿Un i
    o es pern
     Pues se
    ida y se
    Eso es lo
     llamo un
     acción.
     cuánto p
    para la s
     que ese
    uo siga d
    do su ven
    ue en vez
    minarlo s
    a contrar
    su acción
    iendo a a
    , maledic
     otras ba
    emejantes
     que a mí
    iere, deb
    sar que a
    mento no
    provechad
     el tiemp
     libertad
    dando a s
    iete tipo
    onozco. Q
    undo es h
    , es una
    que no ne
    demostrac
    staría un
    para prob
    n todo ca
    un campo
    entración
    pianista
    ó de hamb
    tonces lo
    ron a com
    a rata, p
    a. No es
     sin emba
     lo que q
    ablar aho
    diré más
    e, si hay
    n, algo m
    e este as
     la rata.


In block 19, we see ' he pensa', which we conclude must end with 'do':


```python
bloque19=mensaje[32*(19-1):32*19]
aproach="0"*18+"do".encode("latin-1").hex()+"0"*10

result2=int(bloque19,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b36b9a59d5347"+result2[20:24]+"0"*10
print("Our key would be completed with: " + result2)
```

    Our key would be completed with: 0xb6a59b36b9a59d5347126c0000000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36b9a59d5347126c0000000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:20]
    bloque2=bloque[20:24]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bastará dec
    e soy Juan
     Castel, el
    or que mató
    ría Iribarn
    pongo que e
    ceso está e
    recuerdo de
    s y que no
    cesitan may
    explicacion
    bre mi pers
    Aunque ni e
    blo sabe qu
    lo que ha d
    ordar la ge
    ni por qué.
    ealidad, si
     he pensado
    no hay memo
    olectiva, l
     quizá sea
    orma de def
    de la espec
    mana. La fr
    todo tiempo
    do fue mejo
     indica que
    s sucediera
    os cosas ma
    sino que -f
    ente- la ge
    as echa en
    vido. Desde
    o, semejant
    se no tiene
    dez univers
    o, por ejem
    me caracter
    or recordar
    erentemente
    hechos malo
    así, casi p
     decir que
     tiempo pas
    ue peor", s
    fuera porqu
    presente me
    ce tan horr
    como el pas
    recuerdo ta
    calamidades
    tos rostros
    cos y cruel
    antas malas
    ones, que l
    oria es par
    como la tem
     luz que al
     un sórdido
    o de la ver
    a. ¡Cuántas
    s he quedad
    astado dura
    oras, en un
    ón oscuro d
    ller, despu
     leer una n
    a en la sec
    policial! P
    a verdad es
    no siempre
    s vergonzos
    la raza hum
    parece allí
    ta cierto p
     los crimin
    son gente m
    mpia, más i
    siva; esta
    ación no la
     porque yo
     haya matad
    n ser human
     una honest
    rofunda con
    ón. ¿Un ind
    o es pernic
     Pues se lo
    ida y se ac
    Eso es lo q
     llamo una
     acción. Pi
     cuánto peo
    para la soc
     que ese in
    uo siga des
    do su venen
    ue en vez d
    minarlo se
    a contrarre
    su acción r
    iendo a anó
    , maledicen
     otras baje
    emejantes.
     que a mí s
    iere, debo
    sar que aho
    mento no ha
    provechado
     el tiempo
     libertad,
    dando a sei
    iete tipos
    onozco. Que
    undo es hor
    , es una ve
    que no nece
    demostració
    staría un h
    para probar
    n todo caso
    un campo de
    entración u
    pianista se
    ó de hambre
    tonces lo o
    ron a comer
    a rata, per
    a. No es de
     sin embarg
     lo que qui
    ablar ahora
    diré más ad
    e, si hay o
    n, algo más
    e este asun
     la rata.oH


In block 1, we see 'Bastará dec', which we conclude must end with 'ir':


```python
bloque1=mensaje[0:32]
aproach="0"*22+"ir".encode("latin-1").hex()+"0"*6

result2=int(bloque1,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b36b9a59d5347126c"+result2[24:28]+"0"*6
print("Our key would be completed with: " + result2)
```

    Our key would be completed with: 0xb6a59b36b9a59d5347126cca20000000



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36b9a59d5347126cca20000000"
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:24]
    bloque2=bloque[24:28]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    print(breaking)
```

    Bastará decir
    e soy Juan Pa
     Castel, el p
    or que mató a
    ría Iribarne;
    pongo que el
    ceso está en
    recuerdo de t
    s y que no se
    cesitan mayor
    explicaciones
    bre mi person
    Aunque ni el
    blo sabe qué
    lo que ha de
    ordar la gent
    ni por qué. E
    ealidad, siem
     he pensado q
    no hay memori
    olectiva, lo
     quizá sea un
    orma de defen
    de la especie
    mana. La fras
    todo tiempo p
    do fue mejor"
     indica que a
    s sucedieran
    os cosas mala
    sino que -fel
    ente- la gent
    as echa en el
    vido. Desde l
    o, semejante
    se no tiene v
    dez universal
    o, por ejempl
    me caracteriz
    or recordar p
    erentemente l
    hechos malos
    así, casi pod
     decir que "t
     tiempo pasad
    ue peor", si
    fuera porque
    presente me p
    ce tan horrib
    como el pasad
    recuerdo tant
    calamidades,
    tos rostros c
    cos y crueles
    antas malas a
    ones, que la
    oria es para
    como la temer
     luz que alum
     un sórdido m
    o de la vergü
    a. ¡Cuántas v
    s he quedado
    astado durant
    oras, en un r
    ón oscuro del
    ller, después
     leer una not
    a en la secci
    policial! Per
    a verdad es q
    no siempre lo
    s vergonzoso
    la raza human
    parece allí;
    ta cierto pun
     los criminal
    son gente más
    mpia, más ino
    siva; esta af
    ación no la h
     porque yo mi
     haya matado
    n ser humano:
     una honesta
    rofunda convi
    ón. ¿Un indiv
    o es pernicio
     Pues se lo l
    ida y se acab
    Eso es lo que
     llamo una bu
     acción. Pien
     cuánto peor
    para la socie
     que ese indi
    uo siga desti
    do su veneno
    ue en vez de
    minarlo se qu
    a contrarrest
    su acción rec
    iendo a anóni
    , maledicenci
     otras bajeza
    emejantes. En
     que a mí se
    iere, debo co
    sar que ahora
    mento no habe
    provechado me
     el tiempo de
     libertad, li
    dando a seis
    iete tipos qu
    onozco. Que e
    undo es horri
    , es una verd
    que no necesi
    demostración.
    staría un hec
    para probarlo
    n todo caso:
    un campo de c
    entración un
    pianista se q
    ó de hambre y
    tonces lo obl
    ron a comerse
    a rata, pero
    a. No es de e
     sin embargo,
     lo que quier
    ablar ahora;
    diré más adel
    e, si hay oca
    n, algo más s
    e este asunto
     la rata.oHit


In block 1, we see 'Bastará decir', which we conclude must end with ' qu' since block 2 starts with 'e':


```python
bloque1=mensaje[0:32]
aproach="0"*26+" qu".encode("latin-1").hex()

result2=int(bloque1,16)^int(aproach,16)
result2=hex(result2)
result2="0xb6a59b36b9a59d5347126cca20"+result2[28:34]
print("Our key would be completed with: " + result2)
```

    Our key would be completed with: 0xb6a59b36b9a59d5347126cca202ae43e



```python
n=len(mensaje)
bloque1=mensaje[0:32]
key="0xb6a59b36b9a59d5347126cca202ae43e"
descifrado=[]
for i in range(139):
    bloque=mensaje[32*i:32*(i+1)]
    bloque=int(key,16)^int(bloque,16)
    bloque=hex(bloque)
    bloque1=bloque[2:28]
    bloque2=bloque[28:34]
    bloque1=bytes.fromhex(bloque1).decode('latin-1')
    bloque2=bytes.fromhex(bloque2).decode('latin-1')
    breaking=str(bloque1)+str(bloque2)
    descifrado.append(breaking)
print("".join(descifrado))
```

    Bastará decir que soy Juan Pablo Castel, el pintor que mató a María Iribarne; supongo que el proceso está en el recuerdo de todos y que no se necesitan mayores explicaciones sobre mi persona. Aunque ni el diablo sabe qué es lo que ha de recordar la gente, ni por qué. En realidad, siempre he pensado que no hay memoria colectiva, lo que quizá sea una forma de defensa de la especie humana. La frase "todo tiempo pasado fue mejor" no indica que antes sucedieran menos cosas malas, sino que -felizmente- la gente las echa en el olvido. Desde luego, semejante frase no tiene validez universal; yo, por ejemplo, me caracterizo por recordar preferentemente los hechos malos y, así, casi podría decir que "todo tiempo pasado fue peor", si no fuera porque el presente me parece tan horrible como el pasado; recuerdo tantas calamidades, tantos rostros cínicos y crueles, tantas malas acciones, que la memoria es para mí como la temerosa luz que alumbra un sórdido museo de la vergüenza. ¡Cuántas veces he quedado aplastado durante horas, en un rincón oscuro del taller, después de leer una noticia en la sección policial! Pero la verdad es que no siempre lo más vergonzoso de la raza humana aparece allí; hasta cierto punto, los criminales son gente más limpia, más inofensiva; esta afirmación no la hago porque yo mismo haya matado a un ser humano: es una honesta y profunda convicción. ¿Un individuo es pernicioso? Pues se lo liquida y se acabó. Eso es lo que yo llamo una buena acción. Piensen cuánto peor es para la sociedad que ese individuo siga destilando su veneno y que en vez de eliminarlo se quiera contrarrestar su acción recurriendo a anónimos, maledicencia y otras bajezas semejantes. En lo que a mí se refiere, debo confesar que ahora lamento no haber aprovechado mejor el tiempo de mi libertad, liquidando a seis o siete tipos que conozco. Que el mundo es horrible, es una verdad que no necesita demostración. Bastaría un hecho para probarlo, en todo caso: en un campo de concentración un ex pianista se quejó de hambre y entonces lo obligaron a comerse una rata, pero viva. No es de eso, sin embargo, de lo que quiero hablar ahora; ya diré más adelante, si hay ocasión, algo más sobre este asunto de la rata.oHitVUr
