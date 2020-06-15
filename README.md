# WiresharkKerberosPKIDissector
Wireshark Kerberos PKI Dissector 

Kerberos changed for PKI:
	packet-kerberos.c (changed 
		  case KERBEROS_PA_PK_AS_REP:
			offset=dissect_ber_octet_string_wcb(FALSE, actx, sub_tree, tvb, offset,hf_index, dissect_pkinit_PaPkAsRepConstructedType);
			from dissect_pkinit_PaPkAsReq to dissect_pkinit_PaPkAsRepConstructedType)
	packet-pikinit.c (changed and added isWin2k for old pkauthenticator and also dissect_pkinit_PaPkAsRepConstructedType for padata type 17)
	packet-pikinit.h (Added new function for type 17 of kerberos pki response dissect_pkinit_PaPkAsRepConstructedType)
	packet-x509sat.c (only in dissect_x509sat_CountryName chnged to BER_UNI_TAG_BMPString)
	packet-cms.c (only changed dissect_cms_T_eContent at call_ber_oid_callback to set authpack in correct path)
