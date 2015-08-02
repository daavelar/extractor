#!/usr/bin/php
<?php 

require __DIR__.'/vendor/autoload.php';

$url = $argv[1];

$client = new GuzzleHttp\Client();
$page = $client->get($url);

$dom = new DOMDocument;

libxml_use_internal_errors(true);
$dom->loadHTML($page->getBody());
libxml_clear_errors();

foreach ($dom->getElementsByTagName('img') as $node)
{
  copy($node->getAttribute('src'), 'files/' . uniqid() . '.jpg');
  echo 'Downloading file ' . $node->getAttribute('src') . "\n";
}

