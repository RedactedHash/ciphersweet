# CipherSweet

[![Linux Build Status](https://travis-ci.org/paragonie/ciphersweet.svg?branch=master)](https://travis-ci.org/paragonie/ciphersweet)
[![Latest Stable Version](https://poser.pugx.org/paragonie/ciphersweet/v/stable)](https://packagist.org/packages/paragonie/ciphersweet)
[![Latest Unstable Version](https://poser.pugx.org/paragonie/ciphersweet/v/unstable)](https://packagist.org/packages/paragonie/ciphersweet)
[![License](https://poser.pugx.org/paragonie/ciphersweet/license)](https://packagist.org/packages/paragonie/ciphersweet)
[![Downloads](https://img.shields.io/packagist/dt/paragonie/ciphersweet.svg)](https://packagist.org/packages/paragonie/ciphersweet)

**CipherSweet** is a backend library developed by [Paragon Initiative Enterprises](https://paragonie.com)
for implementing [searchable field-level encryption](https://paragonie.com/blog/2017/05/building-searchable-encrypted-databases-with-php-and-sql).

CipherSweet was originally intend for use in in [SuiteCRM](https://github.com/salesagility/SuiteCRM)
and related products, although there is nothing preventing its use in other products.

Before adding searchable encryption support to your project, make sure you understand
the [appropriate threat model](https://adamcaudill.com/2016/07/20/threat-modeling-for-applications/)
for your use case. At a minimum, you will want your application and database
server to be running on separate cloud instances / virtual machines.
(Even better: Separate bare-metal hardware.)

**Requires PHP 5.5+**, although 7.2 is recommended for better performance.

CipherSweet is available under the very permissive [ISC License](https://github.com/paragonie/ciphersweet/blob/master/LICENSE)
which allows you to use CipherSweet in any of your PHP projects, commercial
or noncommercial, open source or proprietary, at no cost to you.

## CipherSweet Features at a Glance

* Encryption that targets the 256-bit security level
  (using [AEAD](https://tonyarcieri.com/all-the-crypto-code-youve-ever-written-is-probably-broken) modes
  with extended nonces to minimize users' rekeying burden).
* **Compliance-Specific Protocol Support.** Multiple backends to satisfy a
  diverse range of compliance requirements. More can be added as needed:
  * `ModernCrypto` uses [libsodium](https://download.libsodium.org/doc/), the de
    facto standard encryption library for software developers.
  * `FIPSCrypto` only uses the cryptographic algorithms covered by the
    FIPS 140-2 recommendations to avoid auditing complexity.
* **Key separation.** Each column is encrypted with a different key, all of which are derived from
  your master encryption key using secure key-splitting algorithms.
* **Key management integration.** CipherSweet supports integration with Key
  Management solutions for storing and retrieving the master encryption key.
* **Searchable Encryption.** CipherSweet uses
  [blind indexing](https://paragonie.com/blog/2017/05/building-searchable-encrypted-databases-with-php-and-sql#solution-literal-search)
  with the fuzzier and Bloom filter strategies to allow fast ciphertext search
  with minimal data leakage. 
  * Each blind index on each column uses a distinct key from your encryption key
    and each other blind index key.
* **Adaptability.** CipherSweet has a database- and product-agnostic design, so
  it should be easy to write an adapter to use CipherSweet in any PHP-based
  software.

## Installing CipherSweet

Use Composer.

```bash
composer require paragonie/ciphersweet
```

## Using CipherSweet

Please refer to **[the documentation](https://github.com/paragonie/ciphersweet/tree/master/docs)**
to learn how to use CipherSweet.

## Integration Support

Please feel free to [create an issue](https://github.com/paragonie/ciphersweet/issues/new)
if you'd like to integrate CipherSweet with your software.
