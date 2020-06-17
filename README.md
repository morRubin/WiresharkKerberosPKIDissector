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


Negoex
	packet-negoex.c parse PKU2U
	packet-kerberos.c - add dissect_kerberos_Applications_pku2u that calls dissect_kerberos_AS_REQ and mark pku2u
	packet-kerberos.h - add dissect_kerberos_Applications_pku2u signature to use in packet-negoex.c
	packet-pkinit.c - add dissect_pkinit_PaPkAsReq_pku2u to set pku2u and dissect_pkinit_PaPkAsRepConstructedType_pku2u for response
	packet-pkinit.h - add dissect_pkinit_PaPkAsReq_pku2u header to set pku2u from packet-kerberos.c and dissect_pkinit_PaPkAsRepConstructedType_pku2u
	packet-x509ce.c - added new dissector for pku2u sids inside of the certificate for OID 1.3.6.1.4.1.311.90.1
	packet-ber.c - parse sids differently per OID 1.3.6.1.4.1.311.90.1
