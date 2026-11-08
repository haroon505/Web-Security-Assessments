# Loyal Hit - CSRF Account-Edit Assessment

[Read the PDF report](LoyalHit_CSRF_Assessment_Public.pdf)

**Outcome: no CSRF bypass observed in the reported tests.**

| Item | Detail |
| --- | --- |
| Assessor | Haroon Shahid |
| Record | LH-CSRF-001 |
| Target | `https://loyalhit.com` |
| Endpoint | `POST /my-account/edit-account/` |
| Probe | `account_display_name=csrf1` |
| CSRF parameter | `save-account-details-nonce` |

Manual token-mutation checks did not produce a saved display-name change. This is an assessment record; no vulnerability is confirmed.

## Test results

| Test | Request change | Observation |
| --- | --- | --- |
| Incorrect token | One character changed in the valid token | No display-name change |
| Missing token | Entire token parameter removed | No display-name change |
| Empty token | Token value left empty | No display-name change |
| Token substitution | Alternate token used; source not recorded | No display-name change |

## Interpretation and limits

The results are consistent with nonce validation. A successful unmodified valid-token replay and the substituted token's source and validity were not documented. Response captures, cross-site browser proof and sensitive-action impact are not included.

Retain this as an assessment record. No severity rating is assigned. These checks do not establish the security of other account actions or the site as a whole.

## Original request

The complete request structure is reproduced below with sensitive values replaced. All header names, cookie names and form fields are retained. Sensitive values use labels. The original Content-Length is retained; placeholder lengths differ.

**Public edition:** login cookies, the account email and the token value are replaced with labels.

```http
POST /my-account/edit-account/ HTTP/2
Host: loyalhit.com
Cookie: sbjs_migrations=[COOKIE_01]; sbjs_current_add=[COOKIE_02]; sbjs_first_add=[COOKIE_03]; sbjs_current=[COOKIE_04]; sbjs_first=[COOKIE_05]; sbjs_udata=[COOKIE_06]; _ga=[COOKIE_07]; _clck=[COOKIE_08]; _pin_unauth=[COOKIE_09]; trustedsite_visit=[COOKIE_10]; trustedsite_tm_float_seen=[COOKIE_11]; cmplz_consented_services=[COOKIE_12]; cmplz_policy_id=[COOKIE_13]; cmplz_marketing=[COOKIE_14]; cmplz_statistics=[COOKIE_15]; cmplz_preferences=[COOKIE_16]; cmplz_functional=[COOKIE_17]; cmplz_banner-status=[COOKIE_18]; _lscache_vary=[COOKIE_19]; wordpress_logged_in_ec7609858040e8f026d7f7807fa85cde=[COOKIE_20]; wfwaf-authcookie-ec7609858040e8f026d7f7807fa85cde=[COOKIE_21]; _ga_K9QCXBZG4V=[COOKIE_22]; g_state=[COOKIE_23]; sbjs_session=[COOKIE_24]; _clsk=[COOKIE_25]
Content-Length: 314
Cache-Control: max-age=0
Sec-Ch-Ua: "Not:A-Brand";v="8", "Chromium";v="156", "Google Chrome";v="156"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/156.0.0.0 Safari/537.36
Origin: https://loyalhit.com
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/jxl,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://loyalhit.com/my-account/edit-account/
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Priority: u=0, i

account_first_name=Haroon&account_last_name=Shahid&account_display_name=[ORIGINAL_DISPLAY_NAME]&account_email=[TEST_EMAIL_A]&password_current=&password_1=&password_2=&save-account-details-nonce=[CSRF_TOKEN_A]&_wp_http_referer=%2Fmy-account%2Fedit-account%2F&save_account_details=Save+changes&action=save_account_details
```
